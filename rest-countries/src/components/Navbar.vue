<script setup>
import { computed, ref } from 'vue'

const title = ref('Where In the world?')

const colourScheme = ref(false)

const colourMode = computed(() => {
  return colourScheme.value ? 'Dark Mode' : 'Light Mode'
})

function toggleColour() {
  colourScheme.value = !colourScheme.value
}

</script>

<template>
  <nav>
    <p>{{ title }}</p>
    <p @click="toggleColour">{{ colourMode }}</p>
  </nav>
</template>

<style scoped>
nav {
  display: flex;
  justify-content: space-between;
}

p {
  padding: 1em 5em;
  font-weight: 800;
  font-style: normal;
}
</style>