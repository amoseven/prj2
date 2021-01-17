<script>
export default {
  name: 'Comment',
  props: {
    comment: Object
  }
}
</script>

<template>
  <div>
    <p><strong>{{ comment.email }}</strong></p>
    <small>{{ comment.body }}</small>
  </div>
</template>
