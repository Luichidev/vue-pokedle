<script setup>
  import HomeView from './views/HomeView.vue'
  import OneLetter from './components/OneLetter.vue';
</script>

<template>
  <main>
    <HomeView />
    <OneLetter color='green' letter='A'/>
    <OneLetter color='gold' letter='B'/>
    <OneLetter color='grey' letter='C'/>
    <OneLetter />

  </main>
</template>
