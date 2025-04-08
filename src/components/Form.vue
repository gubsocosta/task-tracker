<template>
  <div class="box">
    <div class="columns">
      <div
          class="column is-8"
          role="form"
          aria-label="Form to create a new task"
      >
        <input type="text" class="input" placeholder="What task you want to create?"/>
      </div>
      <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">
          <section>
            <strong>{{ elapsedTime }}</strong>
          </section>
          <button class="button" @click="startStopWatcher">
            <span class="icon">
              <i class="fa fa-play"></i>
            </span>
            <span>Play</span>
          </button>
          <button class="button" @click="stopStopWatcher">
            <span class="icon">
              <i class="fa fa-stop"></i>
            </span>
            <span>Stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue';

const stopWatcher = ref(0);
const timeInSeconds = ref(0);
const elapsedTime = computed(() => new Date(timeInSeconds.value * 1000).toISOString().substring(11,19));

function startStopWatcher () {
  stopWatcher.value = setInterval(() => {
    timeInSeconds.value += 1;
  }, 1000)
}

function stopStopWatcher () {
  clearInterval(stopWatcher.value);
}
</script>

<style scoped lang="sass">

</style>
