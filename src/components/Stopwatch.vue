<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <StopwatchDisplay :time-in-seconds="timeInSeconds"/>
    <StopwatchButton
      icon="fa-play"
      title="Start"
      @click="startStopwatch"
      :disabled="isStopwatchRunning"
    />
    <StopwatchButton
      icon="fa-stop"
      title="Stop"
      @click="stopStopwatch"
      :disabled="!isStopwatchRunning"
    />
  </div>
</template>

<script setup lang="ts">
import StopwatchButton from '@/components/StopwatchButton.vue';
import StopwatchDisplay from '@/components/StopwatchDisplay.vue';
import { ref } from 'vue';

const emit = defineEmits(['stopwatchStopped']);

const setIntervalInstance = ref(0);
const timeInSeconds = ref(0);
const isStopwatchRunning = ref(false);

function startStopwatch () {
  isStopwatchRunning.value = true;
  setIntervalInstance.value = setInterval(() => {
    timeInSeconds.value += 1;
  }, 1000);
}

function stopStopwatch () {
  clearInterval(setIntervalInstance.value);
  isStopwatchRunning.value = false;
  emit('stopwatchStopped', timeInSeconds.value);
  timeInSeconds.value = 0;
}
</script>

<style scoped lang="sass">

</style>
