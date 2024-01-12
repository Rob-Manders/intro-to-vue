<template>
  <div class="score-container">
    <p class="score-header">Score</p>
    <p class="score">{{ score }}</p>
  </div>
</template>

<script setup>
const props = defineProps(['score'])
</script>

<style>
.score-container {
  margin-top: 1.5rem;
  text-align: center;
}

.score-header {
  font-size: 1.5rem;
  margin: 0;
}

.score {
  font-weight: 700;
  font-size: 3.75rem;
  color: #ebeb90;
  margin: 0.5rem;
}
</style>
