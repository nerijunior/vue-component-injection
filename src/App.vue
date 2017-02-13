<template>
  <div id="app">
    <div class="container">
      <main-nav></main-nav>
      <windows></windows>
    </div>
  </div>
</template>

<script>
import MainNav from './components/shared/MainNav'
import Windows from './components/shared/Windows'

import Bus from './bus'

export default {
  name: 'app',
  components: {
    MainNav,
    Windows
  }
}
</script>

<style>
</style>
