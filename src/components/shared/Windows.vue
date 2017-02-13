<template>
  <div id="windows">
    <div class="tabs">
      <ul>
        <li v-for="(tab, index) in tabs"
        :class="{'is-active' : (index == selectedTab)}"
        @click.prevent="changeTab(index)">
          <a>{{ tab.title }}</a>
        </li>
      </ul>
    </div>

    <div class="content">
      <div v-for="(tab, index) in tabs" v-show="(index == selectedTab)">
        <div :id="'base-window-' + index" ></div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import Bus from '../../bus'

export default {
  data () {
    return {
      tabs: [],
      selectedTab: false
    }
  },
  methods: {
    changeTab (index) {
      this.selectedTab = index
    }
  },
  mounted () {
    const vue = this

    Bus.$on('create-window', function (submenu) {
      const index = vue.tabs.push({ title: submenu.title })
      setTimeout(() => {
        const vm = new Vue(submenu.component).$mount('#base-window-' + (index-1))
        vue.selectedTab = index-1
      }, 0)
    })
  }
}
</script>

<style scoped>
</style>
