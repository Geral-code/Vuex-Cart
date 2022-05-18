<template>
  <td colspan="2">Total Producto</td>
  <td> {{ totalCantidad }}</td>
  <td>
      <button 
      class="btn btn-warning btn-sm"
      @click="cancelarOrden"
    
       >
      Cancelar Orden</button>
  </td>
  <td class="font-weight-bold">
      <span>{{Intl.NumberFormat().format(totalPrecio)}} </span>
  </td>
</template>

<script>
import { useStore } from 'vuex';
import { computed } from 'vue';

export default {
    setup() {
        const store = useStore();
        
        // Llamar a los getters
        const totalCantidad = computed( () => store.getters.totalCantidad) ;
        const totalPrecio = computed( () => store.getters.totalPrecio) ;

        // Accion de cancelar orden 
        const cancelarOrden = () => store.commit('setCancelarOrden');

        return {
            totalCantidad,
            totalPrecio,
            cancelarOrden
        }
    }

}
</script>

<style>

</style>