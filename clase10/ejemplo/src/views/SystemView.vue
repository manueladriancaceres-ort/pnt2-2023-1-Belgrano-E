<template>
  <ion-page>
    <ion-content>
      <h2>System Page</h2>
      <ion-list v-for="e in lista" :key="e.id">
        {{ e.id }} {{ e.nombre }}
        <ion-button @click="eliminar(e.id)">Eliminar</ion-button>
        <ion-button @click="modificar(e.id)">Modificar</ion-button>
      </ion-list>  
      <ion-input v-if="ocultar" v-model="elemento.id" label="Codigo"></ion-input>
      <ion-input v-if="ocultar" v-model="elemento.nombre" label="Nombre"></ion-input>
      <ion-button @click="cargarLista">Cargar Lista</ion-button>
      <ion-button @click="agregaraLista">Agregar</ion-button>
      <ion-button @click="ordenarLista">Ordenar</ion-button>
      <ion-button @click="iraHome">Ir a home</ion-button>
    </ion-content>
  </ion-page>
</template>

<script>
import {IonPage, IonButton, IonContent, IonInput, IonList} from '@ionic/vue'
import axios from 'axios'
import listaService from '../services/listaService'

export default {
  components: {IonPage, IonButton, IonContent, IonInput, IonList},
  methods: {
    iraHome() {
      this.$router.push("/")
    },
    async agregaraLista() {
      // Falta control de ingreso de datos
      try {
        const elemento = {...this.elemento}
        await listaService.agregar(elemento)
        await this.cargarLista()
        this.elemento = {}
      } catch(e) {
        alert(e)  
      }  
    },
    ordenarLista() {
      this.lista.sort( (a,b) => a.id - b.id  )
    },
    async cargarLista() {
      try {
        const respuesta = await listaService.cargarLista()
        this.lista = respuesta
      } catch(e) {
        alert(e)  
      }
    },
    async eliminar(id) {
      try {
        await listaService.eliminar(id)
        await this.cargarLista()
      } catch( e) {
        alert('Se produjo un error')
      }
    },
    async modificar(id) {
      try {
        const elemento = {...this.elemento}
        await listaService.modificar(id,elemento)
        await this.cargarLista()
        this.elemento = {}
      } catch( e) {
        alert('Se produjo un error')
      }
    }
  },
  data() {
    return {
      lista: [],
      elemento: {},
      ocultar: true
    }
  }
}
</script>

<style>

</style>