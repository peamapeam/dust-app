<template>
  <div id="app">
    <Chartjs />
  </div>
</template>

<script>
import Chartjs from './components/Chartjs.vue'

export default {
  name: 'app',
  components: {
    Chartjs
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
