<template>
  <div class="col-12 col-sm-4 col-md-3 col-lg-2 mb-3">
    <div class="card">
      <img class="card-img-top" :src="producto.thumbnailUrl" :alt="`imagen-${producto.title}`">
      <div class="card-body">
        <h4 class="card-title">{{ producto.title }}</h4>
        <p class="card-text">$ <span>{{ producto.precio }}</span></p>
        <button type="button" class="btn btn-dark" @click="agregar(producto)">Comprar</button>
      </div>
    </div>
  </div>
</template>

<script>
import { useStore } from 'vuex'

export default {
  props: [
    'producto'
  ],
  setup() {
    const store = useStore()
    const agregar = producto => {
      store.dispatch('agregarAlCarro', producto)
    }

    return {
      agregar
    }
  }
}
</script>
