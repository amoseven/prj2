<script>

import axios from 'axios'
import ResumeMaker from '@/components/ResumeMaker'
import ResumeComponent from '@/components/ResumeComponent'
import CommentsList from '@/components/CommentsList'

export default {
  name: 'MainApp',
  data () {
    return {
      comments: [],
      resume: [],
      loading: false,
      url: 'https://jsonplaceholder.typicode.com/comments?_limit=42',
      db: 'https://vue3-resume-project-default-rtdb.firebaseio.com/resume.json'
    }
  },
  methods: {
    async addItem (block) {
      try {
        const {data} = await axios.post(this.db, block)
        this.resume.push({
          id: data.name,
          ...block
        })
      } catch (e) {
        console.error(e)
      }
    },
    async getComments () {
      try {
        this.loading = true
        const {data} = await axios.get(this.url)
        this.comments = data
      } catch (e) {
        console.error(e)
      } finally {
        this.loading = false
      }
    },
    async getResume () {
      try {
        const {data} = await axios.get(this.db)
        if (data) {
          this.resume = Object.keys(data).map(key => {
            return {
              id: key,
              ...data[key]
            }
          })
        }
      } catch (e) {
        console.error(e.message)
      }
    }
  },
  async mounted () {
    await this.getResume()
  },
  components: {ResumeComponent, ResumeMaker, CommentsList}
}
</script>

<template>
  <div class="container column">
    <resume-maker @add-item="addItem"></resume-maker>

    <div class="card card-w70">
      <resume-component :resume="resume"></resume-component>
    </div>
  </div>

  <div class="container">
    <comments-list @get-comments="getComments"
                   :comments="comments"
                   :loading="loading"></comments-list>
  </div>
</template>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
