<script>
export default {
  props:{
    product: {
      type: Object,
      default: ()=> ({
        name: '',
        cost: 0,
      })
    },
    hideName: {
      type: Boolean,
    }
  }
}

</script>

<template>
  <div>
    <p>Установите цену товара:</p>
    <span v-if="!hideName">{{product.name}}</span>
    <span>{{product.cost}}</span>
    <v-slider min="0" max="500" step="50" :model-value="product.cost" @update:model-value="$emit('update-cost', $event)"/>
  </div>
</template>

<style scoped>

</style>
