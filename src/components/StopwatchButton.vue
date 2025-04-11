<template>
  <button class="button" :disabled="props.disabled" @click="$emit('click')">
      <span class="icon">
        <i :class="['fa', props.icon]"></i>
      </span>
    <span>{{ props.title }}</span>
  </button>
</template>

<script setup lang="ts">
type IconType = 'fa-play' | 'fa-stop';
type TitleType = 'Start' | 'Stop';

const props = defineProps<{
  icon: IconType;
  title: TitleType;
  disabled: boolean;
}>();

defineEmits(['click']);
</script>

<style scoped lang="sass">

</style>
