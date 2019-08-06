<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <FormatBalance />
  </div>
</template>

<script>
import FormatBalance from './components/FormatBalance.vue'

export default {
  name: 'app',
  components: {
    FormatBalance
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
