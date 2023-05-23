<script>
import { RouterLink, RouterView } from 'vue-router'
import {IonApp, IonHeader} from '@ionic/vue'
export default {
  components: {IonApp, IonHeader}
}
</script>

<template>
  <ion-app>
    <ion-header>
      <RouterLink to="/">Home |</RouterLink>
      <RouterLink to="/about">About |</RouterLink>
      <RouterLink to="/system">System</RouterLink>
    </ion-header>
    <RouterView />
  </ion-app>

</template>

<style>
</style>
