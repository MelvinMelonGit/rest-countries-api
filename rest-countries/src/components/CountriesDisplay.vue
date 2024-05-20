<script setup>
import { ref } from 'vue'
import Country from './Country.vue'

</script>

<template>
  <main>
    <Country />
  </main>
</template>

<style scoped>
main {
  background-color: hsl(0, 0%, 98%);
  min-height: 100vh;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
  padding: 5em;
}
</style>