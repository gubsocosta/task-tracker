<template>
  <div class="box form">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Form to create a new task"
      >
        <input
          type="text"
          class="input"
          placeholder="What task you want to create?"
          v-model="taskDescription"
        />
      </div>
      <div class="column">
        <Stopwatch @stopwatch-stopped="endTask"/>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Stopwatch from '@/components/Stopwatch.vue';
import type ITask from '@/types/ITask.ts';
import { ref } from 'vue';

const emit = defineEmits(['saveTask']);

const taskDescription = ref('');

function endTask(durationInSeconds: number) {
  const task: ITask = {
    description: taskDescription.value,
    durationInSeconds,
  };

  emit('saveTask', task);
  taskDescription.value = '';
}
</script>

<style>
.form {
  color: var(--text-primary);
  background-color: var(--bg-primary);
}
</style>
