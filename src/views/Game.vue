<template>
  <div>
    <h1>Крестики-нолики</h1>
    <Board />
    <div v-if="winner">{{ winner }} победил!</div>
    <button @click="resetGame">Начать заново</button>
  </div>
</template>

<script>
import Board from './Board.vue';

export default {
  components: {
    Board,
  },
  data() {
    return {
      winner: null,
    };
  },
  methods: {
    handleWinner(winner) {
      this.winner = winner;
    },
    resetGame() {
      this.$refs.board.resetGame();
      this.winner = null;
    },
  },
};
</script>
