<template>
  <div>
    <b-button
      v-if="products.length > 0"
      variant="success"
      size="m"
      class="mb-2"
      id="show-btn"
      v-b-modal.modal-xl
      @click="$bvModal.show('bv-modal-example')"
    >
      <b-icon icon="cart-check-fill" aria-hidden="true"></b-icon>
      {{ products.length }}
    </b-button>
    <b-button
      v-else
      variant="secondary"
      size="m"
      class="mb-2"
      id="show-btn"
      v-b-modal.modal-xl
      @click="$bvModal.show('bv-modal-example')"
    >
      <b-icon icon="cart-fill" aria-hidden="true"></b-icon>
      {{ products.length }}
    </b-button>

    <b-modal id="modal-xl" size="xl" hide-footer>
      <template #modal-title>Carrito de compras </template>
      <div class="d-block text-center">
        <h3 v-if="products.length > 0"></h3>

        <h3 v-else>Aún no tienes nada en el carrito</h3>
        <CarProducts :products="products" />
        <!-- Tabla productos -->
      </div>
      <h2>Total: {{ totalAmount }}</h2>
      <b-button v-if="products.length>0" variant="success" class="mt-3" block
        >Ir al checkout</b-button
      >
    </b-modal>
  </div>
</template>

<script>
import CarProducts from "@/components/Cart/CartProducts.vue";
export default {
  name: "Cart",
  components: {
    CarProducts,
  },
  data() {
    return {
      products: [],
    };
  },
  mounted() {},
  methods: {
    addProduct(product) {
      let i = this.products.findIndex((prod) => prod.id == product.id);
      if (i >= 0) this.products[i].quant += 1;
      else {
        product.quant = 1;
        this.products.push(product);
      }
    },
  },
  computed: {
      totalAmount(){
            let total = this.products.reduce((accum,item) => accum + (item.quant * item.price), 0)
            return total
      }
  }
};
</script>

<style scoped>
.cart {
  background-color: black;
  width: 100px;
  height: auto;
  right: 0;
  position: absolute;
}
</style>
