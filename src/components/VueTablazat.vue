<template>
  <tr>
      <td v-if="!edit">{{title}}</td>
      <td v-if="edit"><input type="text" v-model="title"></td>

      <td v-if="!edit">{{price}}</td>
      <td v-if="edit"><input type="text" v-model="price"></td>

      <td v-if="!edit">{{quantity}}</td>
      <td v-if="edit"><input type="text" v-model="quantity"></td>

      <td v-if="!edit"><button @click="Edit">Edit</button>
        <button @click="Delete">X</button></td>

      <td v-if="edit"><button @click="Save">Save</button></td>
      <td v-if="!edit">{{quantity*price}}</td>
  </tr>
</template>

<script>
export default {
    props: ['Tabla'],
    data() {
        return {
            title: this.Tabla.title,
            price: this.Tabla.price,
            quantity: this.Tabla.quantity,
            edit: false,
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit('Tabla-valtoztatas', {
                original: this.Tabla,
                new: {
                    title: this.title,
                    price: this.price,
                    quantity: this.quantity
                    },
            })
        },
        Delete(){
            this.$emit('Tabla-torles',{original: this.Tabla})
        }
    }
}
</script>