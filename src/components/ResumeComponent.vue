<script>
import TitleComponent from '@/components/TitleComponent'
import AvatarComponent from '@/components/AvatarComponent'
import SubtitleComponent from '@/components/SubtitleComponent'
import TextComponent from '@/components/TextComponent'

export default {
  name: 'ResumeComponent',
  props: {
    resume: {
      type: Array,
      required: true
    }
  },
  components: {
    TitleComponent, AvatarComponent, SubtitleComponent, TextComponent
  }

}
</script>

<template>
  <template v-if="resume.length > 0">
    <template v-for="R in resume" :key="R.id">
      <component
        :is="R.type+'-component'" v-bind="{content: R.text}"
      ></component>
      <hr>
    </template>

  </template>
  <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
</template>
