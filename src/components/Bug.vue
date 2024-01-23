<template>
  <div class="bug-container" @click="score">
    <div class="bug" :class="showing && 'showing'"></div>
    <div class="hiding-place"></div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const showing = ref(false)

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
:root {
  --pop-up-height: -3rem;
}
.bug-container {
  cursor: pointer;
  position: relative;
  display: grid;
  place-items: center;
  width: 10rem;
  height: 10rem;
  margin: 0.5rem;
}

.bug {
  position: absolute;
  width: 5rem;
  height: 5rem;
  border-radius: 50%;
  background-color: antiquewhite;
  bottom: 0;
  transform: translateY(0);
  transition: transform 150ms;
}

.showing {
  transform: translateY(-3rem)
}

.hiding-place {
  position: absolute;
  width: 100%;
  height: 5rem;
  border-radius: 5px;
  background-color: #305e4f;
  bottom: 0;
}
</style>