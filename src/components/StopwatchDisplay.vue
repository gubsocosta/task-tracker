<template>
  <section>
    <strong class="display">{{ elapsedTime }}</strong>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = withDefaults(
  defineProps<{
      timeInSeconds: number
    }>(),
  {
    timeInSeconds: 0
  }
);

const elapsedTime = computed(() => new Date(props.timeInSeconds * 1000).toISOString().substring(11, 19));

</script>

<style scoped>
.display {
  color: var(--text-primary);
}
</style>
