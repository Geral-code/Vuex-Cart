<template>
<Layout>
    <h2>Carrito Producto View</h2>
    <table class="table">
        <thead>
            <tr>
                <th>#</th>
                <th>Item</th>
                <th>Cantidad</th>
                <th>Accion</th>
                <th>Total</th>

            </tr>
        </thead>

        <tbody>
            <!-- renderizar -->
            <Item v-for="item in carrito" :key="item.id" :itemProps="item"/>
        </tbody>
        <tfoot>
            <tr>
                <td colspan="5" v-if="Object.keys(carrito).length==0">Carrito vacio</td>
                <FooterTotal/>
            </tr>
        </tfoot>
    </table>




</Layout>
  
</template>

<script>
import {useStore} from 'vuex';
import {computed} from 'vue';


import { defineAsyncComponent } from 'vue';
export default {
    name: 'CarritoProductoView',
  components: {
    Layout: defineAsyncComponent(()=> import(/*webpackChunkName: "Layout"*/"@/layout/Layout.vue")),
    Item: defineAsyncComponent(() => import (/*webpackChunkName: "Item"*/"@/components/Item.vue")),
    FooterTotal: defineAsyncComponent(() => import (/*webpackChunkName: "FooterTotal"*/"@/components/FooterTotal.vue")),
  },
  setup(){
      const store = useStore();
      const carrito = computed (() => store.state.carrito);

      return {
          carrito
      }


  }

}

    
</script>

<style>

</style>