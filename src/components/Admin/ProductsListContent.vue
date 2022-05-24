<template>
<div>
<ProductsList :products="products"/>
</div>

</template>

<script>
import ProductsList from '@/components/Admin/ProductsList.vue'
export default {
name: "ProductsListContent",
  props:{
      products: {
          type: Array
      }
  },
  components: {
    ProductsList,
  },
}
</script>

<style>

</style>
