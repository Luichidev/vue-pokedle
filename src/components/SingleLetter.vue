<script setup>
  defineProps({
    letter: {
      type: Object,
      default: { name: '', color: 'transparent'},
    },
  })
</script>

<template>
  <div class="letter" :class='[`bg--${letter.color}`]'>
    {{ letter.name }}
  </div>
</template>

<style scoped>
.letter {
    width: 8rem;
    height: 8rem;
    border: 1px solid black;
    font-weight: bold;
    font-size: 6rem;
    padding: 2rem;
  } 

  .bg--transparent {
    background-color: transparent;
  }
  .bg--green {
    background-color: green;
    border: 1px solid green;
    color: #fff;
  }
  .bg--gold {
    background-color: goldenrod;
    border: 1px solid goldenrod;
    color: #fff;
  }
  .bg--grey {
    background-color: grey;
    border: 1px solid grey;
    color: #fff;
  }
</style>