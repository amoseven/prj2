<template>
  <div class="card" v-if="comments.length !==0">
    <h2>Комментарии</h2>
    <ul class="list">
      <li class="list-item" v-for="comment in comments" :key="comment.id">
        <comment :comment="comment"></comment>
      </li>
    </ul>
  </div>
  <p v-else-if="!loading">
    <button class="btn primary"
            @click="$emit('getComments')">Загрузить комментарии
    </button>
  </p>
  <div class="loader" v-else></div>
</template>

<script>
import Comment from '@/components/Comment'

export default {
  name: 'CommentsList',
  emits: ['getComments'],
  props: {
    loading: {
      type: Boolean,
      default: false
    },
    comments: {
      type: Array,
      default: () => ([])
    }
  },
  components: {Comment}
}
</script>

<style scoped>

</style>
