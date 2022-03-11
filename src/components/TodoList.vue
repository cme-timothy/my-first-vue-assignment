<script setup>
import InputBox from "../components/InputBox.vue";
</script>

<template>
  <main class="main">
    <h2 class="title">To-Do List</h2>
    <InputBox />
  </main>
</template>

<style>
.main {
  margin: 8em auto 0 auto;
  max-width: 25em;
}

.title {
  font-size: 2rem;
}
</style>
