<template>
  <div>
    <div class="card" style="width: 18rem">
      <img class="card-img-top" :src="getImgUrl(img)" alt="Card image cap" />
      <div class="card-body">
        <h5>{{ title }}</h5>
        <h6>${{ price }}</h6>
        <p class="card-text">{{ desc }}</p>
        <button v-if="stock>0" type="button" class="btn btn-success" @click="addToCart">Añadir</button>
        <button v-else type="button" class="btn btn-danger">Agotado</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted (){
  },
  props: {
    id: {
      type: Number,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    desc: {
      type: String,
      required: true,
    },
    price: {
      type: Number,
      required: true,
    },
    img: {
      type: String,
      required: true,
    },
    highlight: {
      type: Boolean,
      required: false,
    },
    stock: {
      type: Number,
      required: true,
    },
  },
  methods: {
    getImgUrl(imgUrl) {
      return require(`@/assets/img/${imgUrl}`);
    },
    addToCart(){
        this.$emit('add-to-cart', this.id)
    }
  },
};
</script>

<style scoped>
/*
* Autor: ropreller
* Año: 2022
* Desc: CSS customizado para ajustes.
*/

.imgTabla {
  max-width: 100px;
}

.noDisponible {
  color: red;
}

.tdNoDisponible {
  background-color: rgb(226, 226, 226);
}
</style>
