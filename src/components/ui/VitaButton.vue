<script lang="ts">
import {defineComponent, PropType} from 'vue'
export default defineComponent({
  name: "VitaButton",
  props:{
    type: {
      type: String as PropType<'add' | 'del'>,
      default: 'add',
    }
  },
  computed: {
    btnConfig(){

      return{
        class: `btn--${this.type}`,
      }
    }
  }
})
</script>

<template>
  <button :class="btnConfig.class">
    <slot/>
    <img class="icon" src="/src/assets/icons/plus-icon.svg" alt="+">
  </button>
</template>

<style scoped lang="scss">
  .btn--add, .btn--del{
    background: linear-gradient(180deg, #4FC3F7 0%, #2979FF 100%);
    width: 162px;
    height: 34px;
    outline: none;
    border: none;
    border-radius: 36px;
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    margin-left: auto;
    box-shadow: 0 2px 4px 0 #78909C5C;
    color: #FFFFFF;
    .text{
      font-size: 15px;
      font-weight: 300;
    }
  }
  .btn--add:disabled{
    opacity: 0.5;
  }
  .btn--del{
    background: #FF5252;
    .icon{
      transform: rotate(45deg);
    }
  }
</style>
