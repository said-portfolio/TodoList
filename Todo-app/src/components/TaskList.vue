<template>
  <v-card class="mb-4 todo-list" outlined flat>
    <v-card-title class="text-h5">Tasks</v-card-title>
    <v-card-text>
      <v-list>
        <v-list-item v-for="(task, index) in tasks" :key="index">
          <v-row class="d-flex align-center">
            <v-col cols="auto mb-2 mt-2">
              <v-btn class="custom-color-3" @click="() => $emit('edit', index)" icon="mdi-pencil-outline" size="small">
                <v-icon left>mdi-pencil-outline</v-icon>
              </v-btn>
            </v-col>
            <v-col cols="auto">
              <v-btn class="custom-color-5" @click="() => $emit('delete', index)" icon="mdi-trash-can-outline" size="small">
                <v-icon left>mdi-trash-can-outline</v-icon>
              </v-btn>
            </v-col>
            <v-col>
              <div v-if="editIndex !== index">{{ task }}</div>
              <v-text-field v-else v-model="editText" @blur="() => saveEdit(index)" dense hide-details @keyup.enter="() => saveEdit(index)" />
            </v-col>
          </v-row>
        </v-list-item>
      </v-list>
    </v-card-text>
  </v-card>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue';

const props = defineProps({
  tasks: {
    type: Array,
    required: true
  },
  editIndex: {
    type: Number,
    default: null
  }
});

const emits = defineEmits(['edit', 'delete', 'save']);

const editText = ref<string>('');

watch(() => props.editIndex, (newIndex) => {
  if (newIndex !== null) {
    editText.value = props.tasks[newIndex] as string;
  }
});

const saveEdit = (index: number) => {
  if (editText.value.trim() !== '') {
    emits('save', { index, text: editText.value });
  }
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
.custom-color-3 {
  background-color: #03a9f4;
  color: white;
}
.custom-color-5 {
  background-color: #f44336;
  color: white;
}
</style>