<script setup>
import LogIn from './components/LogIn.vue'
</script>

<template>
  <main>
    <div class="wrapper">
       <LogIn/>
    </div>
  </main>
</template>

<style scoped>
.wrapper {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  /* height: 80vh;   */
  flex-direction: column; 
  gap: 10px;
  background-color: aquamarine;
}
</style>
