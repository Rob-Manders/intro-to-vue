<template>
  <h1>My Component</h1>

  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
  <p>{{ sum }}</p>
</template>

<script setup>
function add(x, y) {
  return x + y
}

const sum = add(2, 3)
</script>

<style scoped>
h1 {
  font-family: 'Gloria-Hallelujah'
}
</style>