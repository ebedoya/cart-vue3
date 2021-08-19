<template>
  <div class="container">
    <h1>Carrito de Compras</h1>
    <hr>
    <Carrito/>
    <div class="row">
      <Card 
        v-for="producto of productos" 
        :key="producto.id"
        :producto="producto"
      />
    </div>
  </div>
</template>

<script>
import { useStore } from 'vuex'
import { computed, onMounted } from '@vue/runtime-core'

import Card from './components/Card'
import Carrito from "./components/Carrito";

export default {
  name: 'App',
  components: {
    Carrito,
    Card
  },
  setup() {
    const store = useStore()

    onMounted(() => {
      store.dispatch('fetchData')
    })

    const productos = computed(() => store.state.productos)
    // const carrito = computed(() => store.state.carrito)

    return {
      productos
    }
  }
}
</script>

<style>

</style>
