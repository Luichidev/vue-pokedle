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

    let result = arrayUserWord.map((letter, i) => {
      if (letter === arrayWord[i]) {
        arrayWord[i] = ' '
        return { name: letter, color: 'green' }
      }
    })
    
    arrayUserWord.forEach((letter, i) => {
      if (arrayWord.includes(letter)) {
        result[i] = { name: letter, color: 'gold' }
      } else if(arrayWord[i] !== ' '){
        result[i] = { name: letter, color: 'grey' }
      }
    })
    
    return result
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
    gap: 8px;
    margin-block-end: 8px;
  }
</style>