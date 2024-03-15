<script lang="ts">
import {defineComponent} from 'vue'
import {cloneDeep} from "lodash"
export default defineComponent({
  name: "VitaProductAdd",
  props: {
    productCount: {
      type: Number,
      required: true
    }
  },
  data(){
    return{
      product: {
        name: '',
        cost: 0,
      },
      products: [],
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
    <VitaPrice class="mt-3" hide-name @update-cost="product.cost = $event" :product="product" />
    <p class="list">Список добавленных товаров:</p>
    <v-col class="mt-3">
      <v-row class="align-center justify-space-between">
        <span class="num">{{productCount}}</span>
        <input
          type="text"
          class="name"
          placeholder="Введите название"
          v-model="product.name"
        />
        <span class="counter">{{product.cost}} ₽</span>
      </v-row>
    </v-col>
    <VitaButton class="mt-3" :disabled="isButtonDisabled" type="add" @click="addProduct">
      Добавить товар
    </VitaButton>
  </VitaCard>
</template>

<style scoped>
  .list{
    font-size: 15px;
    font-weight: 300;
    color: #78909C;
  }
  .num{
    margin-right: 6px;
  }
  .name{
    outline: none;
    border: 1px solid #00BCD4;
    border-radius: 6px;
    padding: 3px 6px;
    height: 24px;
    text-align: left;
    width: 225px;
    color: #78909C;
  }

  .counter{
    padding: 2px 8px;
    border: 1px solid #00BCD4;
    border-radius: 6px;
    font-size: 15px;
    color: #78909C;
    font-weight: 300;
    margin-left: auto;
  }
</style>
