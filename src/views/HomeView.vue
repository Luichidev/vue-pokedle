<script setup>
  import { ref } from 'vue'
  import GameBox from '../components/GameBox.vue'
  import SearchForm from '../components/SearchForm.vue'
  import { wordDay } from '../api';

  const userWord = ref(null)
  
  const handleAddUserWord = (word) => {
    userWord.value = word
  }
</script>

<template>
  <h1>POKEDLE</h1>
  <GameBox :word='wordDay' :user-word='userWord'/>
  <SearchForm :long='wordDay.length' @user:word='handleAddUserWord'/>
</template>

<style scoped>
  h1 {
    font-size: 4rem;
  }
</style>