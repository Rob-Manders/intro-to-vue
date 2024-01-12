<template>
  <Header />

  <main>
    <Score :score="score" />

    <div class="bugs">
      <Bug />
    </div>
  </main>
</template>

<script setup>
import Header from './components/Header.vue'
import Score from './components/Score.vue'
import Bug from './components/Bug.vue'

const score = 7
</script>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
