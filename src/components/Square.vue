<template>
    <button class="square" @click="handleClick">
      {{ value }}
    </button>
  </template>
  
  <script>
  export default {
    props: {
      value: String,
    },
    methods: {
      handleClick() {
        this.$emit('click');
      },
    },
  };
  </script>
  
  <style scoped>
 
  .square {
    width: 50px;
    height: 50px;
    font-size: 1.5em;
    border: 1px solid #ddd;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }
  
  </style>
  