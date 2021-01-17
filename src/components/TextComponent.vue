<template>
  <p>{{ content }}</p>
</template>

<script>
export default {
  props: {
    content: {
      type: String,
      required: true
    }
  },
  name: 'TextComponent'
}
</script>

<style scoped>

</style>
