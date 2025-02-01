<template>
  <v-card class="mb-2" outlined flat>
    <v-card-text>
      <v-row class="d-flex align-center">
        <v-col cols="auto" class="flex-grow-1" style="max-width: 80%;">
          <v-text-field v-model="textFieldValue" label="Todo Item" dense hide-details />
        </v-col>
        <v-col cols="auto">
          <v-btn class="custom-color-1" @click="textFieldValueSave" icon="mdi-check" size="small" />
        </v-col>
        <v-col cols="auto">
          <v-btn class="custom-color-3" @click="textFieldValueEdit" icon="mdi-pencil-outline" size="small" :disabled="isButtonDisabled"/>
        </v-col>
        <v-col cols="auto">
          <v-btn class="custom-color-5" @click="textFieldValueDelete" icon="mdi-trash-can-outline" size="small" :disabled="isButtonDisabled"/>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const textFieldValue = ref<string>('');

const isButtonDisabled = computed(() => {
  return textFieldValue.value.trim() === '';
});

const textFieldValueSave = () => {
  console.log('---->', textFieldValue.value);
};

const textFieldValueEdit = () => {
  // Edit logic here
};

const textFieldValueDelete = () => {
  // Delete logic here
};
</script>

<style scoped>
.mb-2 {
  margin-bottom: 16px;
}
.d-flex {
  display: flex;
}
.align-center {
  align-items: center;
}
.flex-grow-1 {
  flex-grow: 1;
}
</style>
