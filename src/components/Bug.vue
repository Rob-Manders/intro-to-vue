<template>
  <div class="bug-container">
    <div class="bug" :class="showing && showingClass"></div>
    <div class="hiding-place"></div>
  </div>
</template>

<script setup>
const showingClass = "showing"
let showing = true


</script>

<style scoped>
:root {
  --pop-up-height: -3rem;
}
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
  width: 5rem;
  height: 5rem;
  border-radius: 50%;
  background-color: antiquewhite;
  bottom: 0;
  transform: translateY(0);
  transition: transform 250ms;
}

.showing {
  transform: translateY(-3rem)
}

.hiding-place {
  position: absolute;
  width: 100%;
  height: 5rem;
  border-radius: 5px;
  background-color: rgb(48, 94, 79);
  bottom: 0;
}
</style>