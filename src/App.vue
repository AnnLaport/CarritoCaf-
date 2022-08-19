<template>
  <div class="container">
      <HelloWorld msg="CRUD Café"/>
      <ProductosComp />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ProductosComp from './components/ProductosComp.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    ProductosComp
}
}
</script>

