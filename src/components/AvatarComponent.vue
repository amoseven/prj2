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

<template>
  <div class="avatar">
    <img :src="content"/>
  </div>
</template>
