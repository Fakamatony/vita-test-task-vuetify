<template>
  <v-app>
    <v-main class="pa-16">
      <v-row>
        <v-col>
          <VitaProductAdd :product-count="productCount" @add="addProduct"/>
        </v-col>
        <v-col>
          <VitaProductList @delAll="clearList" @del="delProduct" :products="products"/>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script >

import VitaCard from "./components/VitaCard.vue";

export default {
  data(){
    return{
      products: JSON.parse(localStorage.getItem('products')) || []
    }
  },
  computed: {
    productCount() {
      return this.products.length +1;
    }
  },
  methods:{
    addProduct(product){
      this.products.push(product)
      this.saveToLocalStorage()
      console.log(this.products.length)
    },
    delProduct(index){
      this.products.splice(index, 1)
      this.saveToLocalStorage()
    },
    clearList(index){
      this.products.length = 0
      this.saveToLocalStorage()
    },

    saveToLocalStorage() {
      localStorage.setItem('products', JSON.stringify(this.products))
    }
  },
  watch: {
    products: {
      handler() {
        this.saveToLocalStorage()
      },
      deep: true
    }
  }
}

</script>

<style lang="scss">

</style>
