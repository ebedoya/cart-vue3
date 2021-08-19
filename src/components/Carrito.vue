<template>
  <div class="my-5">
    <h4>Crrito de compras</h4>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Item</th>
          <th scope="col">Cantidad</th>
          <th scope="col">Acción</th>
          <th scope="col">Total</th>
        </tr>
      </thead>
      <tbody id="items">
      <Item
        v-for="item in items" :key="item.id"
        :item="item"
      />
      </tbody>
      <tfoot>
        <tr id="footer-carrito">
          <th scope="row" colspan="5" v-if="Object.keys(items).length === 0">Carrito vacío...</th>
          <Footer v-else />
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>
import { useStore } from 'vuex'
import { computed } from "vue"
import Item from "./Item"
import Footer from "./Footer"

export default {
  components: {
    Footer,
    Item
  },
  setup() {
    const store = useStore()
    const items = computed(() => store.state.carrito)

    return {
      items
    }
  }
}
</script>