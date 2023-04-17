<template>
  <div>
    Nuevos roles
    <li v-for="r in roles" v-bind:key="r">
      {{ r }}
    </li>
    <input type="text" v-model="nRol">
    <button v-on:click="agregarRol">Agregar rol</button>
  </div>
</template>

<script>
export default {
    props: ['roles'],
    data() {
        return {
            nRol: ''
        }
    },
    methods: {
        agregarRol() {
            this.$emit("agregarRolHijo",this.nRol)
        }
    }
}
</script>

<style>

</style>