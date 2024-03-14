<script setup lang="ts">
import Logo from '@/assets/icons/icon.svg'

</script>

<template>
  <v-card color="white" class="pa-3" rounded="3">
    <v-sheet color="blue" class="pa-2" rounded="1_5">
      <v-img width="98px" :src="Logo"/>
    </v-sheet>
    <slot/>
  </v-card>
</template>

<style scoped lang="scss">
</style>
