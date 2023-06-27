<template>
  <div class="container">
    <h1>Carrito</h1>
    {{ carrito }}
    <hr />
    <div class="row">
      <Card
        v-for="producto in productos"
        :key="producto.id"
        :producto="producto"
      />
    </div>
  </div>
</template>

<script>
import { useStore } from "vuex";
import { computed, onMounted } from "vue";
import Card from "./components/Card.vue";
export default {
  name: "App",
  components: {
    Card,
  },

  setup() {
    const store = useStore();
    onMounted(() => {
      store.dispatch("fetchData");
    });

    const productos = computed(() => store.state.productos);
    const carrito = computed(() => store.state.carrito);
    return { productos, carrito };
  },
};
</script>
