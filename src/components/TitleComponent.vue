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

<template>
  <h1>{{ content }}</h1>
</template>
