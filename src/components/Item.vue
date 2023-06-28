<template>
  <tr>
    <th scope="row">{{ item.id }}</th>
    <td>{{ item.title }}</td>
    <td>{{ item.cantidad }}</td>
    <td>
      <button
        class="btn btn-info btn-sm mx-1 rounded"
        @click="aumentar(item.id)"
      >
        ➕
      </button>
      <button
        class="btn btn-danger btn-sm mx-1 rounded"
        @click="disminuir(item.id)"
      >
        ➖
      </button>
    </td>
    <td>$ {{ item.precio * item.cantidad }}</td>
  </tr>
</template>

<script>
import { useStore } from "vuex";
export default {
  props: ["item"],
  setup() {
    const store = useStore();
    const aumentar = (id) => {
      store.commit("aumentar", id);
    };

    const disminuir = (id) => {
      store.commit("disminuir", id);
    };
    return { aumentar, disminuir };
  },
};
</script>
