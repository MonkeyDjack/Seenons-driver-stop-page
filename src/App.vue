<template>
  <Header/>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: rgb(50,126,134);
  background: linear-gradient(90deg, rgba(50,126,134,1) 0%, rgba(76,193,149,1) 100%);
}
.container {
  min-width: 320px;
  max-width: 800px;
  margin: 0 auto;
}
</style>
