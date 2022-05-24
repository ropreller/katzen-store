<template>
  <div>
    <b-table striped hover :items="items"></b-table>

  </div>
</template>

<script>
export default {
  props:{
      products: {
          type: Array
      }
  },
  data() {
    return {
      items: this.products

    };
  },
};
</script>

<style>
</style>
