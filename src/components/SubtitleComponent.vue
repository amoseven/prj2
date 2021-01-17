<script>
export default {
  props: {
    content: {
      type: String,
      required: true
    }
  },
  name: 'SubtitleComponent'
}
</script>

<template>
  <h2>{{ content }}</h2>
</template>
