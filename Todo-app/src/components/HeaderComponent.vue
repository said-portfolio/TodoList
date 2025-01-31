<template>
  <v-layout>
    <v-card>
      <v-app-bar>
        <v-toolbar-title>My Todo App</v-toolbar-title>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </v-app-bar>
    </v-card>
  </v-layout>
</template>

<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<style lang="scss" scoped>
/* Add your styles here */
</style>
