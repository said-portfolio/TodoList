<template>
  <v-container class="pa-4">
    <v-card class="mb-4" outlined flat>
      <v-card-title class="text-h5">Create New Task</v-card-title>
      <v-card-text>
        <v-row class="d-flex align-center">
          <v-col cols="auto" class="flex-grow-1" style="max-width: 80%;">
            <v-text-field 
              v-model="textFieldValue" 
              label="Todo Item" 
              dense 
              hide-details 
              @keyup.enter="textFieldValueSave" 
            />
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>

    <TaskList 
      :tasks="tasks" 
      :editIndex="editIndex" 
      @edit="textFieldValueEdit" 
      @delete="textFieldValueDelete" 
      @save="saveEdit" 
    />
  </v-container>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue';
import TaskList from '@/components/TaskList.vue';

const textFieldValue = ref<string>('');
const tasks = ref<string[]>([]);
const editIndex = ref<number | undefined>(undefined);

const isButtonDisabled = computed(() => {
  return textFieldValue.value.trim() === '';
});

const textFieldValueSave = () => {
  if (textFieldValue.value.trim() !== '') {
    const currentTasks = JSON.parse(localStorage.getItem('tasks') || '[]');
    currentTasks.push(textFieldValue.value);
    localStorage.setItem('tasks', JSON.stringify(currentTasks));
    tasks.value = currentTasks;
    textFieldValue.value = ''; // Clear the input field after saving
  }
};

const textFieldValueEdit = (index: number) => {
  editIndex.value = index;
};

const saveEdit = ({ index, text }: { index: number, text: string }) => {
  if (text.trim() !== '') {
    tasks.value[index] = text;
    localStorage.setItem('tasks', JSON.stringify(tasks.value));
  }
  editIndex.value = undefined;
};

const textFieldValueDelete = (index: number) => {
  const currentTasks = JSON.parse(localStorage.getItem('tasks') || '[]');
  currentTasks.splice(index, 1);
  localStorage.setItem('tasks', JSON.stringify(currentTasks));
  tasks.value = currentTasks;
};

onMounted(() => {
  const storedTasks = JSON.parse(localStorage.getItem('tasks') || '[]');
  tasks.value = storedTasks;
});
</script>

<style scoped>
.pa-4 {
  padding: 16px;
}
.mb-4 {
  margin-bottom: 16px;
}
.custom-color-1 {
  background-color: #6200ea;
  color: white;
}
</style>
