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
      Удалить все
    </VitaButton>
    <div class="d-flex align-center justify-start mt-4 container" v-for="(product, index) in products " :key="index">
      <p>{{index +1}}.</p>
      <p class="ml-1">{{product.name}}</p>
      <div class="d-flex ml-auto ga-2 align-center">
        <p>{{product.cost}} ₽</p>
        <div class="del-button" @click="$emit('del', index)"><img src="/src/assets/icons/trash-icon.svg" alt="del"></div>
      </div>
    </div>
  </VitaCard>
</template>

<style scoped>
  .container{
    color: #212121;
    font-weight: 200;
  }
  .del-button{
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
