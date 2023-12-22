<template>
  <div id="app">
    <Board />
  </div>
</template>

<script>
import Board from './components/Board.vue';

export default {
  components: {
    Board,
  },
};
</script>

<style>
/* глобальные стили по желанию */
body {
  font-family: 'Arial', sans-serif;
  text-align: center;
  margin: 20px;
}

h1 {
  color: #333;
}
</style>
