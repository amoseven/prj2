<template>
  <h1>{{ content }}</h1>
</template>

<script>
export default {
  name: 'TitleComponent',
  props: {
    content: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
