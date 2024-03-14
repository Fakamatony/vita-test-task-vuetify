<script lang="ts">
import {defineComponent} from 'vue'
import {cloneDeep} from "lodash"
export default defineComponent({
  name: "VitaProductAdd",
  data(){
    return{
      product: {
        name: '',
        cost: 0,
      }
    }
  },
  computed: {
    isButtonDisabled() {
      return this.product.name === '' || this.product.cost === 0
    }
  },
  methods: {
    addProduct(){
      this.$emit('add', cloneDeep(this.product))
      this.product.name = ''
      this.product.cost = 0
    }
  }

})
</script>

<template>
  <VitaCard>
    <VitaPrice hide-name @update-cost="product.cost = $event" :product="product" />
    <VitaButton :disabled="isButtonDisabled" type="add" @click="addProduct">
      Добавить
    </VitaButton>
    <v-text-field v-model="product.name"/>
  </VitaCard>
</template>

<style scoped>

</style>
