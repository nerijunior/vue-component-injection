<template>
  <div id="vendas-relatorio">
    <h1>{{ title }}</h1>
    <button class="button is-primary" @click.prevent="change">Change Title</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: 'Relatório'
    }
  },
  methods: {
    change () {
      this.title = 'New Title'
    }
  }
}
</script>

<style scoped>
</style>
