<template>
  <ion-page>
    <ion-content>
      <h2>Login</h2>
      <ion-input v-model="usuario.email" label="Email" type="email"></ion-input>
      <ion-input v-model="usuario.passw" label="Password" type="password"></ion-input>
      <ion-button @click="logear">Login</ion-button>
    </ion-content>  
  </ion-page>
</template>

<script>
import { IonPage, IonButton, IonContent, IonInput } from "@ionic/vue";
import { useLoginStore } from "../stores/login";

export default {
  components: { IonPage, IonButton, IonContent, IonInput },
  setup() {
    const store = useLoginStore();
    const { login } = store;
    return { login };
  },
  data() {
    return {
      usuario: {email:'',passw:''}
    }
  },
  methods: {
    logear() {
        // hardcodeo hasta la classe que viene
        // proxima clase conexion con backend
        if (this.usuario.email=="test@test.com" && this.usuario.passw=="123456") {
          this.login( { email: this.usuario.email, permissions: [] } )
          this.$router.push('system')
        } else if (this.usuario.email=="admin@test.com" && this.usuario.passw=="123456") {
          this.login( { email: this.usuario.email, permissions: ['config'] } )
          this.$router.push('config')
        } else {
          alert('Credenciales incorrectas')
        }  
    }
  }
};
</script>

<style>
</style>
