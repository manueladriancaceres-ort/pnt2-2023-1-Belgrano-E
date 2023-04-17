<template>
  <div>
    <h2>{{titulo}}</h2>
    Usuario: {{usuario}}
    <br/>
    <Roles :roles="roles" @agregarRolHijo="agregarRol"/>
  </div>
</template>

<script>
import Roles from './Roles.vue'
export default {
    data() {
        return {
            titulo: 'Home',
            roles: ['ADM','ENCARGADO','USUARIO']
        }
    },
    components: {
      Roles
    },
    props: ['usuario'],
    methods: {
      agregarRol(nRol) {
        this.roles.push(nRol)
      }
    }
}
</script>

<style>

</style>