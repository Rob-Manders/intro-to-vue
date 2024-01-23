<template>
  <Header />

  <main>
    <StartButton v-if="!gameStarted" @click="startGame" />

    <div class="game-container" v-if="gameStarted">
      <Score :score="score" />
      
      <div class="bugs">
        <Bug
          v-for="index in numberOfBugs"
          :key="index"
          @scored="updateScore"
        />
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue'
import StartButton from './components/StartButton.vue'
import Score from './components/Score.vue'
import Bug from './components/Bug.vue'

const numberOfBugs = 3

const gameStarted = ref(false)
const score = ref(0)

function startGame() {
  gameStarted.value = true
}

function updateScore() {
  score.value += 1
}
</script>

<style scoped>
main {
  text-align: center;
}
.game-container {
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
