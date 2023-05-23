<template>
  <!-- break hasta 21:20-->
  <ion-page>
    <ion-content>
      <h2>System Page</h2>
      <ion-list v-for="e in lista" :key="e.id">
        {{ e.id }} {{ e.nombre }}
      </ion-list>  
      <ion-input v-model="elemento.id" label="Codigo"></ion-input>
      <ion-input v-model="elemento.nombre" label="Nombre"></ion-input>
      <ion-button @click="agregaraLista">Agregar</ion-button>
      <ion-button @click="ordenarLista">Ordenar</ion-button>
      <ion-button @click="iraHome">Ir a home</ion-button>
    </ion-content>
  </ion-page>
</template>

<script>
import {IonPage, IonButton, IonContent, IonInput, IonList} from '@ionic/vue'
export default {
  components: {IonPage, IonButton, IonContent, IonInput, IonList},
  methods: {
    iraHome() {
      this.$router.push("/")
    },
    agregaraLista() {
      this.lista.push({...this.elemento})
      this.elemento = {}
    },
    ordenarLista() {
      this.lista.sort( (a,b) => a.id - b.id  )
    }
  },
  data() {
    return {
      lista: [{id:101,nombre:'Carlos'},{id:100,nombre:'Roxana'},],
      elemento: {}
    }
  }
}
</script>

<style>

</style>