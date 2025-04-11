<template>
  <main :class="['columns','is-gapless', 'is-multiline', { 'dark-mode': isDarkModeActive}]">
    <div class="column is-one-quarter">
      <SideBar @toggle-dark-mode="toggleDarkMode" />
    </div>
    <div class="column is-three-quarter content">
      <Form @save-task="saveTask"/>
      <div class="task-list">
        <TaskItem v-for="(task, index) in taskList" :key="index" :task="task"/>
        <BoxCard v-if="!taskList.length">
          You are not productive today :(
        </BoxCard>
      </div>
    </div>
  </main>
</template>

<script setup lang="ts">
import BoxCard from '@/components/BoxCard.vue';
import Form from '@/components/Form.vue';
import SideBar from '@/components/SideBar.vue';
import TaskItem from '@/components/TaskItem.vue';
import type ITask from '@/types/ITask.ts';
import { ref } from 'vue';

const taskList = ref<ITask[]>([]);
const isDarkModeActive = ref(false);

function saveTask (task: ITask) {
  taskList.value.push(task);
}

function toggleDarkMode () {
  isDarkModeActive.value = !isDarkModeActive.value;
}
</script>

<style scoped>
.task-list {
  padding: 1.25rem;
}

main {
  --bg-primary: #eee;
  --text-primary: #222;
}

main.dark-mode {
  --bg-primary: #2b2d42;
  --text-primary: #ddd;
}

.content {
  background: var(--bg-primary);
  color: var(--text-primary);
}
</style>
