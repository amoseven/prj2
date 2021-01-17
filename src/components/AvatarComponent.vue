<template>
  <div class="avatar">
    <img :src="content"/>
  </div>
</template>

<script>
export default {
  props: {
    content: {
      type: String,
      required: true
    }
  },
  name: 'AvatarComponent'
}
</script>

<style scoped>

</style>
