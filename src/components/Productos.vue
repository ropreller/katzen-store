<template>
  <div>
       <div>
    <table class="table">
            <thead>
                <tr>
                    <th v-for="(item, i) in titles" :key="i" scope="col">{{ item }}</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, i) in products" :key="i">
                   <td>{{ item.id }}</td>
                   <td>{{ item.price }}</td>
                   <td><img :src="item.img" class="imgTabla" /></td>
                   <td>{{ item.name }}</td>
                   <td>{{ item.desc }}</td>
                   <td>{{ item.stock }}</td>
                   <td>
                   <button v-if="item.stock>0" type="button" class="btn btn-success">Añadir</button>
                   <p v-else class="noDisponible">No disponible</p>
                   </td>
                </tr>
            </tbody>
        </table>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        titles: {
            type: Array,
            required: true
        },
        products: {
            type: Array,
            required: true
        },
    }
}
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
    color:red
}

.tdNoDisponible {
    background-color: rgb(226, 226, 226);
}

</style>
