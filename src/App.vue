<template>
  <div id="app">
    <Header />
    <Songs />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Songs from './components/Songs.vue'
export default {
  name: 'App',
  components: {
    // HelloWorld,
    Songs,
    Header
  }
}
</script>

<style lang="scss">
@import "./style/commons.scss"; //da questo file si importa bootstrap
</style>
