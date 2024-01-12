<template>
  <Header />

  <main>
    <Score :score="score" />

    <div class="bugs">
      <Bug v-for="index in numberOfBugs" :key="index" />
    </div>
  </main>
</template>

<script setup>
import Header from './components/Header.vue'
import Score from './components/Score.vue'
import Bug from './components/Bug.vue'

const numberOfBugs = 6
const score = 7
</script>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.bugs {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  align-items: center;
  margin-top: 1.5rem;
  max-width: 600px;
}
</style>
