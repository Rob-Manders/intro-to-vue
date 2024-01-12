<template>
  <p class="score-header">Score</p>
  <p class="score">{{ score }}</p>
</template>

<script setup>
const props = defineProps(['score'])
</script>

<style>
.score {
  font-size: 3rem;
}
</style>
