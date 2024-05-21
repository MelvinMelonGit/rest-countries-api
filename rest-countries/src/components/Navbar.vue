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
    <div>
      <h1>{{ title }}</h1>
      <p @click="toggleColour">{{ colourMode }}</p>
    </div>
  </nav>
</template>

<style scoped>
nav {
  padding: 2em 0;
  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1)
}

div {
  display: flex;
  justify-content: space-between;
  width: 80%;
  margin: 0 auto;
}

h1, p {
  font-weight: 800;
  font-style: normal;
}
</style>