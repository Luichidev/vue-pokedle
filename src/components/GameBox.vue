<script setup>
  import { watch, ref, computed } from 'vue'
  import SingleWord from '../components/SingleWord.vue'

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

  const LIVES = 5
  const isWord = ref(false)
  const userWord = computed(() => props.userWord)
  const arrayUserWord = computed(() => new Array(LIVES).fill("").map(() => ""))
  
watch(userWord, () => {
  if (!arrayUserWord.value.includes(props.userWord)){
    arrayUserWord.value.unshift(props.userWord)
    arrayUserWord.value.length = LIVES
    isWord.value = true
  }
})
</script>

<template>
  <div v-if="!isWord">
    <div v-for="ele in LIVES" :key='ele'>
      <SingleWord :word='word'/>
    </div>
  </div>
  <div v-else>
      <SingleWord v-for="userWord in arrayUserWord" :key='userWord' :word='word' :user-word='userWord' />
  </div>
</template>