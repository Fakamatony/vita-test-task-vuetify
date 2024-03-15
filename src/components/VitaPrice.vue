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
  <div class="container">
    <p class="price">Установите цену товара:</p>
    <span class="name" v-if="!hideName">{{product.name}}</span>
    <span class="cost">{{product.cost}} ₽</span>
      <v-slider
        color="#00BCD4"
        thumb-color="white"
        track-color="grey"
        thumb-size="40px"
        track-size="20px"
        rounded="3"
        class="w-100 justify-center ml-auto pl-6 pr-6"
        min="0"
        max="500"
        step="50"
        :model-value="product.cost"
        @update:model-value="$emit('update-cost', $event)"
      />
  </div>
</template>

<style scoped>
  .container{
    display: flex;
    flex-direction: column;
    gap: 12px;
    margin-top: 12px;
  }

  .name{
    font-size: 20px;
    font-weight: 400;
  }

  .price{
    font-size: 15px;
    color: #78909C;
    font-weight: 300;
  }
  .cost{
    font-size: 32px;
    font-weight: 500;

  }
</style>
