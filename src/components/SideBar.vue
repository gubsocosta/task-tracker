<template>
  <header>
    <h1>
      <img src="@/assets/logo.jpg" alt="">
    </h1>
    <button type="button" class="button" @click="$emit('toggleDarkMode')">
      Toggle Dark Mode
    </button>
  </header>
</template>

<script setup lang="ts">
defineEmits(['toggleDarkMode']);
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
