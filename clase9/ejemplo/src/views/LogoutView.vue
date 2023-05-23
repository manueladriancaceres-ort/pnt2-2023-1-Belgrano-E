<template>
  <ion-page>
    <h2>Logout</h2>
    <ion-button @click="unlogear">Logout</ion-button>
  </ion-page>
</template>

<script>
import { IonPage, IonButton } from "@ionic/vue";
import { useLoginStore } from "../stores/login";

export default {
  components: { IonPage, IonButton },
  setup() {
    const store = useLoginStore();
    const { logout } = store;
    return { logout };
  },
  methods: {
    unlogear() {
        this.logout()
        this.$router.push('/login')
    }
  }
};
</script>

<style>
</style>
