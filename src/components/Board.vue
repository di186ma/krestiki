<template>
    <div>
      <h1>Крестики-нолики</h1>
      <div class="board">
        <div v-for="(row, rowIndex) in board" :key="rowIndex" class="board-row">
          <Square
            v-for="(value, colIndex) in row"
            :key="colIndex"
            :value="value"
            @click="handleClick(rowIndex, colIndex)"
          />
        </div>
      </div>
      <p v-if="winner">{{ winner === 'Draw' ? 'Ничья' : `Победитель: ${winner}` }}</p>
    </div>
  </template>

<script>
import Square from './Square.vue';

export default {
  components: {
    Square,
  },
  data() {
    return {
      board: Array(3).fill().map(() => Array(3).fill(null)),
      xIsNext: true,
      winner: null,
    };
  },
  methods: {
    handleClick(row, col) {
      if (this.board[row][col] || this.winner) {
        return;
      }

      this.board[row][col] = this.xIsNext ? 'X' : 'O';
        this.xIsNext = !this.xIsNext;
        this.winner = this.calculateWinner(this.board);
      },
      calculateWinner(board) {
  const lines = [
    [0, 0, 0, 1, 0, 2], // top row
    [1, 0, 1, 1, 1, 2], // middle row
    [2, 0, 2, 1, 2, 2], // bottom row
    [0, 0, 1, 0, 2, 0], // left column
    [0, 1, 1, 1, 2, 1], // middle column
    [0, 2, 1, 2, 2, 2], // right column
    [0, 0, 1, 1, 2, 2], // main diagonal
    [0, 2, 1, 1, 2, 0]  // secondary diagonal
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c, d, e, f] = lines[i];
    if (board[a][b] && board[a][b] === board[c][d] && board[a][b] === board[e][f]) {
      return board[a][b];
    }
  }
  
  // Проверка на ничью
  let isDraw = true;
  for (let i = 0; i < board.length; i++) {
    for (let j = 0; j < board[i].length; j++) {
      if (!board[i][j]) {
        isDraw = false;
        break;
      }
    }
    if (!isDraw) {
      break;
    }
  }
  
  if (isDraw) {
    return 'Draw';
  }
  
  return null;
}
,
  },
};
</script>

  
  
  <style scoped>

  .board {
    display: inline-block;
    border: 1px solid #ddd;
  }
  
  .board-row {
    display: flex;
  }
  

  </style>
  