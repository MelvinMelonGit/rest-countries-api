<script setup>
import { ref } from 'vue'
import Country from './Country.vue'

</script>

<template>
  <main>
    <section>
      <Country />
    </section>
  </main>
</template>

<style scoped>
main {
  display: grid;
  place-items: center;
}

section {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 4em;
  width: 80%;
  background-color: hsl(0, 0%, 98%);
  margin-top: 5em;
}

@media screen and (min-width: 426px) and (max-width: 1024px) {
  section { 
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>