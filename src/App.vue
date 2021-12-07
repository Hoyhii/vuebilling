<template>
  <div id="app">
    <raktar :Tablazat="Tablazat" @Tabla-hozzaadas="Created" @Tabla-valtoztatas="Changed" @Tabla-torles="Deleted" />
  </div>
</template>

<script>
import raktar from './components/VueRaktar.vue'

export default {
  name: 'App',
  components: {
    raktar
  },
  data() {
    return {
      Tablazat: [
        {
          title: 'Kerék',
          price: 100,
          quantity: 12
        },
        {
          title: 'Teleszkóp',
          price: 1000,
          quantity: 300
        },
        {
          title: 'Kormány',
          price: 230,
          quantity: 5
        },
        {
          title: 'Ajtó',
          price: 45120,
          quantity: 321
        },
      ]
    }
  },
  methods: {
    Created(e){
        this.Tablazat.push({title: e.title, price: e.price, quantity: e.quantity})
    },
    Deleted(e){
      this.Tablazat.splice(this.Tablazat.indexOf(e.original), 1);
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
  margin-top: 60px;
}
</style>
