<template>
  <div id="app">
    <Header ref="myHeader" />
    <b-container class="bv-example-row">

      <b-row>
        <Product
          v-for="(item, i) in products"
          :key="i"
          :id="item.id"
          :title="item.title"
          :desc="item.desc"
          :price="item.price"
          :img="item.img"
          :highlight="item.highlight"
          :stock="item.stock"
          @add-to-cart="addToCart"
        />
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Vue from "vue";
import { BootstrapVue, IconsPlugin } from "bootstrap-vue";
// Import Bootstrap and BootstrapVue CSS files (order is important)
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
import Product from "./components/Product/Product.vue";
import Header from "./components/layout/Header.vue";
import Cart from "./components/Cart/Cart.vue";

// Make BootstrapVue available throughout your project
Vue.use(BootstrapVue);
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin);

export default {
  name: "App",
  components: {
    Product,
    Header,
    Cart,
  },
  data() {
    return {
      products: [
        {
          id: 1,
          title: "Churu clásico unidad",
          price: 1500,
          desc: "Clásico churu sabor atún.",
          img: "churu.jpg",
          highlight: false,
          stock: 2,
        },
        {
          id: 2,
          title: "Leonardo atún",
          price: 3500,
          desc: "Exclusivo sabor atún.",
          img: "leonardo.jpg",
          highlight: false,
          stock: 0,
        },
        {
          id: 3,
          title: "Leonardo salmón",
          price: 1500,
          desc: "Sabor salmón ahumado.",
          img: "leonardo_2.jpg",
          highlight: false,
          stock: 2,
        },
        {
          id: 4,
          title: "Mattise exclusive",
          price: 4500,
          desc: "Alto estandar de calidad.",
          img: "mattise.jpg",
          highlight: false,
          stock: 5,
        },
        {
          id: 5,
          title: "Proplan Urinary",
          price: 1500,
          desc: "Para el cuidado renal del michi",
          img: "proplan_urinary.jpg",
          highlight: false,
          stock: 2,
        },
        {
          id: 6,
          title: "Bravery",
          price: 4800,
          desc: "La mejor de todas",
          img: "bravery.jpg",
          highlight: false,
          stock: 0,
        },
      ],
    };
  },
  mounted() {},
  methods: {
    addToCart(id) {
      console.log("id prod", id);
      let result = this.products.find((prod) => {
        return prod.id == id;
      });
      if (result) {
        this.$refs.myHeader.$refs.myCart.addProduct(result);
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
