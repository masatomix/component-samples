<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <ParentView msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import ParentView from './components/ParentView.vue'

export default {
  name: 'app',
  components: {
    ParentView,
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin: 60px;
}
</style>
