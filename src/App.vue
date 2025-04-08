<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <Form />
    </div>
  </main>
</template>

<script setup lang="ts">
import Form from '@/components/Form.vue';
import SideBar from '@/components/SideBar.vue';
</script>

<style scoped lang="sass">
</style>
