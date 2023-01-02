<script setup>
  import { computed } from 'vue'
  import SingleLetter from '../components/SingleLetter.vue'

  const props = defineProps({
    word: {
      type: String,
      required: true,
    },
    userWord: {
      type: String,
      default: '',
    }
  })

  const letters = computed(() => {
    if (!props.userWord) return props.word.split("").map(() => ({ name: '', color: 'transparent'}))

    const arrayWord = props.word.split("")
    const arrayUserWord = props.userWord.split("")

    return arrayUserWord.map(((letter, i) => {
      if (letter === arrayWord[i]) return { name: letter, color: 'green'}
      else if (arrayWord.includes(letter)) return {name: letter, color: 'gold'}
      else return { name: letter, color: 'grey'}
    }))
  })
</script>

<template>
  <div class="word" >
    <SingleLetter v-for="letter in letters" :key='letter' :letter='letter'/>
  </div>
</template>

<style scoped>
  .word {
    display: flex;
  }
</style>