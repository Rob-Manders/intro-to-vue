<template>
  <!-- Header Component -->

  <main>
    <div class="game-container">
      <!-- Score Board -->
      
      <div class="bugs">
        <!-- Bugs -->
      </div>
    </div>
  </main>
</template>

<script setup>

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
