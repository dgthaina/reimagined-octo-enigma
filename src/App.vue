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