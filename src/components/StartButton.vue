<template>
  <button class="start-button">Start!</button>
</template>

<style scoped>
.start-button {
  all: unset;
  cursor: pointer;
  font-size: 1.75rem;
  background-color: #305e4f;
  padding: 0.5rem 1.25rem;
  margin-top: 2rem;
  border-radius: 5px;
  transition: background-color 150ms ease-in-out;
}

.start-button:hover,
.start-button:focus {
  background-color: #af7200;
}
</style>