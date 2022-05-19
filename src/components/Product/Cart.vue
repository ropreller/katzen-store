<template>
<!-- Example single danger button -->
<div class="btn-group">
  <button type="button" class="btn btn-success dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    Carrito ({{ products.length }})
  </button>

  <div class="dropdown-menu">
  </div>
</div>
</template>

<script>
export default {
    name: 'Cart',
    data(){
        return {
            products: [],
        }
    },
    mounted(){
    },
    methods: {
        addProduct(product) {
            let i = this.products.findIndex((prod) => prod.id == product.id)
            if (i >=0) this.products[i].quant +=1
            else {
                product.quant = 1
                this.products.push(product)
            }
            //console.log(`total products ${this.products.quant} .`)
        }
    }

}
</script>

<style scoped>

.cart {
    background-color: black;
    width:100px;
    height:auto;
    right: 0;
    position: absolute;
}

</style>
