<template>
  <div id="app">
    <Phrases/>
  </div>
</template>

<script>
import Phrases from './components/Phrases.vue'

export default {
  name: 'app',
  components: {
    Phrases
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
