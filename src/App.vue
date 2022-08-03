<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from 'vue';
import MainContent from './components/MainContent.vue'

const count = ref(0);

const setCounter = (value) => {
  count.value = value;
}
</script>

<template>
  <h1>Todos({{ count }})</h1>
  <MainContent :setCounter=setCounter />
</template>

<style scoped>
</style>
