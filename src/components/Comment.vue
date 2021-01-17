<template>
  <div>
    <p><strong>{{ comment.email }}</strong></p>
    <small>{{ comment.body }}</small>
  </div>
</template>

<script>
export default {
  name: 'Comment',
  props: {
    comment: Object
  }
}
</script>

<style scoped>

</style>
