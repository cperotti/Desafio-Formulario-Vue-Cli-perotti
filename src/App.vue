<template>
  <div id="app">
    <container-componente />
  </div>
</template>

<script>
import ContainerComponente from './components/ContainerComponente.vue'

export default {
  name: 'App',
  components: {
    ContainerComponente

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
  padding-top: 60px;
  background-color:peachpuff;
}
</style>
