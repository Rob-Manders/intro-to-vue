<template>
  <Header />

  <main>
    <Score :score="score" />

    <div class="bugs">
      <Bug
        v-for="index in numberOfBugs"
        :key="index"
        @scored="updateScore"
      />
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue'
import Score from './components/Score.vue'
import Bug from './components/Bug.vue'

const numberOfBugs = 3

const score = ref(0)

function updateScore() {
  score.value += 1
}
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
