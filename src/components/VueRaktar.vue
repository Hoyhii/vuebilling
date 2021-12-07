<template>
  <table>
      <tr>
          <th><h1>Title</h1></th>
          <th><h1>Price</h1></th>
          <th><h1>Quantity</h1></th>
          <th><h1>Operations</h1></th>
          <th><h1>Items value</h1></th>
      </tr>
        <Tablazat
        v-for="Tabla in Tablazat"
        :key="Tabla.title"
        :Tabla="Tabla"
        @Tabla-valtoztatas="Changed"
        @Tabla-torles="Deleted"
        />
        <tr>
            <td><input type="text" v-model="title"></td>
            <td><input type="number" v-model="price"></td>
            <td><input type="number" v-model="quantity"></td>
            <td><button @click="New">New Line</button></td>
        </tr>
  </table>
</template>

<script>
import Tablazat from './VueTablazat.vue'
export default {
    props: ['Tablazat'],
    data() {
        return {
            title: null,
            price: null,
            quantity: null,
        }
    },
    components: {Tablazat},
    methods: {
        New(){
            this.$emit('Tabla-hozzaadas', {title:this.title,price:this.price,quantity:this.quantity} )
            this.title = null 
            this.price = null 
            this.quantity = null 
        },
        Changed(e) {
            this.$emit('Tabla-valtoztatas', e)
        },
        Deleted(e){
            this.$emit('Tabla-torles', e)
        }
    }
}
</script>