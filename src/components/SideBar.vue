<template>
  <header>
    <h1>
      <img src="@/assets/logo.jpg" alt="">
    </h1>
  </header>
</template>

<script setup lang="ts">

</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
