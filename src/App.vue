<template>
  <component :is="currentView" />
</template>

<script setup>
  import { ref, computed } from 'vue';
  import LoginPage from './pages/LoginPage.vue'
  import MainPage from './pages/MainPage.vue'
  import SubscribePage from './pages/SubscribePage.vue'

  const routes = {
      '/': MainPage,
      'login': LoginPage,
      'subscribe': SubscribePage
  }

  const currentPath = ref(window.location.pathname)

  window.addEventListener('hashchange', () => {
      currentPath.value = window.location.pathname
  })

  const currentView = computed(() => {
      return routes[currentPath.value.slice(1) || '/']
  })

</script>

<style>
   body {
        background-color: #a70000;
        background-image: radial-gradient(#ffffff 0.5px, transparent 0.5px), radial-gradient(#ffffff 0.5px, #a70000 0.5px);
        background-size: 15px 15px;
        font-family: 'Autour One', cursive;
        height: 100vh;  
        overflow-y: hidden;
    }
</style>