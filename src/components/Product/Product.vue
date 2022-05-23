<template>
    <b-col cols="3">
      <b-card-group deck>
        <b-card :title="title" :img-src="getImgUrl(img)" img-alt="Image" img-top>
          <b-card-text>
            {{ desc }}
            ${{ price }}
          </b-card-text>
          <button
            v-if="stock > 0"
            type="button"
            class="btn btn-success"
            @click="addToCart"
          >
            Añadir
          </button>
          <button v-else type="button" class="btn btn-danger">Agotado</button>
          <template #footer>
            <small class="text-muted">test</small>
          </template>
        </b-card>
      </b-card-group>
    </b-col>
</template>

<script>
export default {
  mounted() {},
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
    addToCart() {
      this.$emit("add-to-cart", this.id);
    },
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
