<script lang="ts">
import {defineComponent, PropType} from 'vue'
import Plus from '@/assets/icons/plus-icon.svg'

export default defineComponent({
  name: "VitaButton",
  props:{
    type: {
      type: String as PropType<'add' | 'del'>,
      default: 'add',
    }
  },
  computed: {
    Plus,
    btnConfig(){

      return{
        class: `btn--${this.type}`,
      }
    }
  }
})
</script>

<template>
  <v-btn :class="btnConfig.class">
    <slot/>
    <v-img :src="Plus"/>
  </v-btn>
</template>

<style scoped lang="scss">
  .btn--add{
    background-color: #30A8FF;
  }
  .btn--del{
    background-color: rebeccapurple;
  }
</style>
