<template>
  <div id="app">
    <ShortUrl />
  </div>
</template>

<script>
import ShortUrl from './components/ShortUrl.vue'

export default {
  name: 'app',
  components: {
    ShortUrl
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
