<template>
  <div class="container">
    <h1 class="text-center">Carrito</h1>
    <hr />
    <div class="row">
      <Card
        v-for="producto in productos"
        :key="producto.id"
        :producto="producto"
      />
    </div>
    <Carrito />
  </div>
</template>

<script>
import { useStore } from "vuex";
import { computed, onMounted } from "vue";
import Card from "./components/Card.vue";
import Carrito from "./components/Carrito.vue";
export default {
  name: "App",
  components: {
    Card,
    Carrito,
  },

  setup() {
    const store = useStore();
    onMounted(() => {
      store.dispatch("fetchData");
    });

    const productos = computed(() => store.state.productos);
    return { productos };
  },
};
</script>
