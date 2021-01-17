<template>
  <form class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="typeBlock">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="textBlock"></textarea>
    </div>

    <button class="btn primary"
            @click.prevent="addItem"
            :disabled="!validBlock"
    >Добавить
    </button>
  </form>
</template>

<script>
export default {
  name: 'ResumeMaker',
  emits: {
    'add-item' ({type, text}) {
      if (text.length > 3) {
        return true
      }
      console.warn('Слишком короткое содержимое...', text.length)
      return false
    }
  },
  computed: {
    validBlock () {
      return this.textBlock.length > 3
    }
  },
  data () {
    return {
      typeBlock: 'title',
      textBlock: ''
    }
  },
  methods: {
    addItem () {
      this.$emit('add-item', {
        type: this.typeBlock,
        text: this.textBlock
      })
      this.typeBlock = 'title'
      this.textBlock = ''
    }
  }

}
</script>

<style scoped>

</style>
