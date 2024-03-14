<template>
  <v-app>
    <v-main>
      <v-row>
        <v-col>
          <VitaProductAdd @add="addProduct"/>
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
  components: {VitaCard},
  data(){
    return{
      products: []
    }
  },
  methods:{
    addProduct(product){
      this.products.push(product)
    },
    delProduct(index){
      this.products.splice(index, 1)
    },
    clearList(index){
      this.products.length = 0
    }
  }
}
</script>

<style lang="scss">

</style>
