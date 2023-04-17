<script>
  import Home from './components/Home.vue'
  import Cabecera from './components/Cabecera.vue'
  export default {
    data() {
      return {
        nusuario: 'PNT2'
      }
    },
    components: {
      Home, Cabecera
    }
  }
</script>

<template>
  <div>
    <Cabecera/>
    App
    <Home :usuario="nusuario"/>
  </div>
</template>

<style scoped>
</style>
