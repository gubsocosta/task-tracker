<template>
  <BoxCard>
    <div class="columns">
      <div class="column is-7">
        {{ props.task.description || 'Task without description' }}
      </div>
      <div class="column">
        <StopwatchDisplay :time-in-seconds="props.task.durationInSeconds"/>
      </div>
    </div>
  </BoxCard>
</template>

<script setup lang="ts">
import BoxCard from '@/components/BoxCard.vue';
import StopwatchDisplay from '@/components/StopwatchDisplay.vue';
import type { ITask } from '@/types/ITask.ts';

const props = defineProps<{
  task: ITask
}>();
</script>

<style scoped>
</style>
