<template>
  <div id="app">
    <Header />
    <div class="container">
        <Productos :titles="tableRender.titles" :products="tableRender.products" />
    </div>
  </div>
</template>

<script>
import Productos from './components/Productos.vue'
import Header from './components/layout/Header.vue'

export default {
  name: 'App',
  components: {
    Productos
    ,Header
  },
  data (){
    return {
            tableRender : {
            titles: ['ID','Precio','Foto','Nombre','Descripcion','Stock','Añadir'],
            products: [
                {
                    id: 1,
                    name: 'Churu clásico unidad',
                    price: 1500,
                    desc: 'Clásico churu sabor atún.',
                    img: 'churu.jpg',
                    stock: 2

                },
                {
                    id: 2,
                    name: 'Bravery 7kg.',
                    price: 45000,
                    desc: 'Alimento Bravery sabor salmón.',
                    img: 'bravery.jpg',
                    stock: 0
                },
                {
                    id: 3,
                    name: 'Matisse 7kg.',
                    price: 43200,
                    desc: 'Alimento Mattise sabor salmón.',
                    img: 'mattise.jpg',
                    stock: 3
                },
                {
                    id: 4,
                    name: 'Leonardo lata.',
                    price: 3450,
                    desc: 'Alimento humedo marca exclusiva.',
                    img: 'leonardo.jpg',
                    stock: 7
                },
                {
                    id: 5,
                    name: 'Leonardo kitten.',
                    price: 46200,
                    desc: 'Leonardo kitten sabor inigualable.',
                    img: 'leonardo_2.jpg',
                    stock: 0
                },
                {
                    id: 6,
                    name: 'Proplan urinary.',
                    price: 33600,
                    desc: 'Para el cuidado de sus riñones.',
                    img: 'proplan_urinary.jpg',
                    stock: 1
                }
            ]
        },
    }
  }
}
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
