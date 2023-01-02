<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  long: {
    type: Number,
    required: true,
  }
})

const userWord = ref('')
const emit = defineEmits(['user:word'])

const canSend = computed(() => userWord.value.length === props.long)

const handleClickOnSubmit = () => {
  emit('user:word', userWord.value.toLowerCase())
  userWord.value = ""
}
</script>

<template>
  <div class="form">
    <form @submit.prevent='handleClickOnSubmit'>
      <div class="form__group">
        <input class="form__input" v-model="userWord" type="text">
        <button class="form__submit" :disabled='!canSend' type="submit">enviar</button>
      </div>
    </form>
  </div>
</template>

<style scoped>
.form {
    padding: 4rem 0;
  }

  .form__group {
    position: relative;
    width: 100%;
  }

  .form__input {
    border-radius: 0.5rem;
    width: 100%;
  }

  .form__input,
  .form__submit {
    border: 1px solid #dadada;
    padding: 1rem;
  }

  .form__submit {
    backface-visibility: hidden;
    background-color: #2bc3ff;
    border-top-right-radius: 0.5rem;
    border-bottom-right-radius: 0.5rem;
    cursor: pointer;
    font-weight: bold;
    inset-block-start: 0;
    inset-inline-end: 0;
    position: absolute;
    text-transform: uppercase;
    transition: opacity 0.3s ease;
  }
</style>