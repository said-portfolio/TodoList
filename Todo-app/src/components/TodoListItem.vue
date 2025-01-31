<template>
  <v-text-field v-model="textFieldValue" label="Todo Item" dense hide-details></v-text-field>

  <v-btn class="custom-color-1" @click="textFieldValueSave" icon="mdi-check" size="small" />
  <v-btn class="custom-color-3" @click="textFieldValueEdit" icon="mdi-pencil-outline" size="small" />
  <v-btn class="custom-color-5" @click="textFieldValueDelete" icon="mdi-trash-can-outline" size="small" />
</template>

<script setup lang="ts">
import { ref } from 'vue'

const textFieldValue = ref<string>('')

const textFieldValueSave = () => {
  console.log('---->', textFieldValue.value)
}
const textFieldValueEdit = () => {
  console.log('---->', textFieldValue.value)
}
const textFieldValueDelete = () => {
  console.log('---->', textFieldValue.value)
}
</script>
<style lang="scss" scoped>
.color-1 {
  color: white;
}
</style>
