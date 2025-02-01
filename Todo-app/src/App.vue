<script setup lang="ts">
import { RouterView } from 'vue-router'
import HeaderComponent from '@/components/HeaderComponent.vue'
</script>

<template>
  <v-row>
    <v-col cols="12" class="header-component">
      <HeaderComponent />
    </v-col>
    <v-col cols="12">
      <RouterView />
    </v-col>
  </v-row>
</template>

<style lang="scss" scoped>
.header-component {
 margin-bottom: 5%;
}
</style>
