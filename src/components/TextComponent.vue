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

<template>
  <p>{{ content }}</p>
</template>
