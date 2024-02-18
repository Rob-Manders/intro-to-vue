<template>
  <div class="bug-container" @click="score">
    <img class="bug" :src="bugImage" :class="showing && 'showing'" />
    <img class="hiding-place" src="../assets/images/bush.png" />
  </div>
</template>

<script setup>
import { computed, ref } from 'vue'

import bug1 from '../assets/images/bug-1.png'
import bug2 from '../assets/images/bug-2.png'
import bug3 from '../assets/images/bug-3.png'

const showing = ref(false)
const bugImage = computed(() => {
  const bugs = [bug1, bug2, bug3]
  const imageIndex = Math.floor(Math.random() * 3)

  return bugs[imageIndex]
})

loop()

function loop() {
  const minDelay = !showing.value ? 300 : 1500
  const maxDelay = !showing.value ? 1000 : 5000

  const interval = Math.random() * (maxDelay - minDelay) + minDelay

  showing.value = !showing.value

  setTimeout(loop, interval)
}

// Event Emitter:
const emit = defineEmits(['scored'])

function score() {
  if (showing.value) {
    showing.value = false
    emit('scored')
  }
}
</script>

<style scoped>
.bug-container {
  position: relative;
  display: grid;
  place-items: center;
  width: 10rem;
  height: 10rem;
  margin: 0.5rem;
}

.bug {
  position: absolute;
  height: 4.75rem;
  bottom: 0.25rem;
  transform: translateY(0);
  transition: transform 150ms;
}

.showing {
  transform: translateY(-4rem)
}

.hiding-place {
  position: absolute;
  width: 100%;
  height: 5rem;
  border-radius: 5px;
  bottom: 0;
}
</style>