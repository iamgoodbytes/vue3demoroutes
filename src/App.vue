<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import Home from './components/Home.vue'
import Todo from './components/Todo.vue'

// Check out https://vuejs.org/api/composition-api-setup.html
import { ref, computed, onMounted } from 'vue'

// We create just an object
const routes = {
  '/': Home,
  '/todo': Todo
};

// get the hash from the url, e.g. /#/todo 
let currentPath = ref(window.location.hash);
console.log(currentPath + " is the current path");

// computed properties are derived from other variables, this will return the name of a component 
let currentView = computed(() => routes[currentPath.value.slice(1) || '/'] || Home);
console.log(currentView);

// https://vuejs.org/api/composition-api-lifecycle.html#onmounted
onMounted( () => {
    window.addEventListener('hashchange', () => {
		  currentPath.value = window.location.hash;
      console.log(currentPath.value + " is the current path");
      console.log(currentView);
      
		})
  });
</script>

<template>
  <a href="#/home">Home</a> |
  <a href="#/todo">Todo</a> |
  <a href="#/non-existent-path">Broken Link</a>
  <component :is="currentView" />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
