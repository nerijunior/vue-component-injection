<template>
  <div id="main-nav">
    <nav class="nav has-shadow">
      <div class="container">
        <div class="nav-left">
          <a v-for="category in categories"
          class="nav-item is-tab is-hidden-mobile"
          @click.prevent="selectCategory(category)"
          :class="{'is-active' : selectedCategory == category}">
            {{ category.title }}
          </a>
        </div>
      </div>
    </nav>

     <nav class="nav has-shadow" v-if="selectedCategory">
      <div class="container">
        <div class="nav-left">
          <a v-for="item in selectedCategory.submenu"
          class="nav-item is-tab is-hidden-mobile"
          @click.prevent="showWindow(item)">{{ item.title }}</a>
        </div>
      </div>
    </nav>
    <!-- //.submenu -->
  </div>
</template>

<script>
import Vue from 'vue'
import Bus from '../../bus'
import Clientes from '../cadastro/Clientes.vue'
import Relatorio from '../vendas/Relatorio.vue'

export default {
  data () {
    return {
      selectedCategory: false,
      categories: [
        { title: 'Cadastro', submenu:[ { title: 'Clientes', component: Clientes } ] },
        { title: 'Vendas', submenu:[ { title: 'Relatório', component: Relatorio } ] }
      ]
    }
  },
  methods: {
    showWindow (submenu) {
      Bus.$emit('create-window', submenu)
    },
    selectCategory (category) {
      this.selectedCategory = category
    }
  }
}
</script>

<style scoped>
</style>
