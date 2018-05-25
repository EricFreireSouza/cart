<template>
  <div id="app">
    <Ccheader />
    <router-view/>
  </div>
</template>

<script>
import Ccheader from './components/Ccheader.vue'

export default {
  name: 'App',
  components: {
    Ccheader
  },
  data(){
    return{}
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
}
</style>
