<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="ID del Producto"
        label-for="input-1"
      >
        <b-form-input
          id="input-1"
          v-model="form.id"
          placeholder="Ingrese ID del producto."
          type="number"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-2"
        label="Nombre del producto"
        label-for="input-2"
      >
        <b-form-input
          id="input-2"
          v-model="form.title"
          placeholder="Ingrese el nombre del producto."
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Descripción" label-for="input-3">
        <b-form-input
          id="input-3"
          v-model="form.desc"
          placeholder="Ingrese la descripción del producto"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-4" label="Precio" label-for="input-4">
        <b-form-input
          id="input-4"
          v-model="form.price"
          placeholder="Ingrese el precio"
          type="number"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-5" label="Imagen" label-for="input-5">
        <b-form-input
          id="input-5"
          v-model="form.img"
          placeholder="Ingrese la URL de la imagen"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-7" label="Stock" label-for="input-7">
        <b-form-input
          id="input-7"
          v-model="form.stock"
          placeholder="Ingrese el stock del producto"
          type="number"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-table striped hover :items="items"></b-table>
  </div>
</template>

<script>
export default {
  props: {
    products: {
      type: Array,
    },
  },
  data() {
    return {
      form: {
        id: "",
        title: "",
        desc: "",
        price: "",
        img: "",
        highlight: true,
        stock: "",
      },
      //foods: [{ text: 'Select One', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn'],
      show: true,
      items: this.products
    };
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      this.form.highlight = true
      alert(JSON.stringify(this.form));
      console.log("productos", this.products)
      //this.products.push(JSON.stringify(this.form))
    },
    onReset(event) {
      event.preventDefault();
      // Reset our form values
      this.form.id = "";
      this.form.title = "";
      this.form.desc = "";
      this.form.img = "";
      this.form.price = "";
      //this.form.highlight = [];
      this.form.stock = 0;
      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>
