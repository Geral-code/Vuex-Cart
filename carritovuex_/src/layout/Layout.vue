<template>
  <div class="layout">
      <!-- navbar -->
      <Navbar/>
      <div class="container mt-5">
          <!-- Donde se va a renderizar los componentes -->
          <slot/>

      </div>
  </div>
</template>

<script>
import { defineAsyncComponent } from 'vue';
import Navbar from '@/components/Navbar.vue';

export default {
    name: 'layout',
    components: {
        Navbar: defineAsyncComponent (() => import(/*webpackChunckName: "Navbar"*/'@/components/Navbar.vue'))
    
    }

}
</script>

<style>

</style>