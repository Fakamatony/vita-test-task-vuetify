<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  props: {
    products: {
      type: Array
    }
  },
  name: "VitaProductList",
  data(){
    return{
      product: {
        name: '',
        cost: 0,
      },
    }
  }
})
</script>

<template>
  <VitaCard>
    <VitaPrice v-if="products.length" @update-cost="products[products.length -1].cost=$event" :product="products[products.length -1]" />
    <VitaButton type="del" @click="$emit('delAll')">
      Удалить
    </VitaButton>
    <div v-for="(product, index) in products " :key="index">
      <p>{{index +1}}</p>
      <p>{{product.name}}</p>
      <p>{{product.cost}}</p>
      <v-btn @click="$emit('del', index)">del</v-btn>
    </div>
  </VitaCard>
</template>

<style scoped>

</style>
