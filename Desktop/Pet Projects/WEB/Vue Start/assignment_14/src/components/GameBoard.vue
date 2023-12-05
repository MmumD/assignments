<template>
  <div class="game-board">
    <div class="win" @click="restart" style="display: none;">
      <p>Click to restarts</p>
      <p><span>Winner is:</span> {{currentPlayer}}</p>
    </div>
    <div v-for="(row, rowIndex) in board" :key="rowIndex" class="row">
      <div v-for="(cell, colIndex) in row" :key="colIndex" class="cell" @click="makeMove(rowIndex, colIndex)">
        {{ cell }}
      </div>
    </div>
  </div>
  <div class="info">
    <p><span>Move:</span> {{currentPlayer}}</p>
    <a class="btn" @click="restart">Restart</a>
  </div>

</template>

<script>
export default {
  data() {
    return {
      board: [
        ['', '', ''],
        ['', '', ''],
        ['', '', '']
      ],
      boardSelect: [
        [false, false, false],
        [false, false, false],
        [false, false, false]
      ],
      currentPlayer: 'X'
    };
  },
  methods: {
    makeMove(row, col) {
      if(this.boardSelect[row][col] == false){
        this.board[row][col] = this.currentPlayer;
        if(this.currentPlayer == 'X') this.currentPlayer = 'O';
        else this.currentPlayer = "X"
        this.boardSelect[row][col] = true;
        this.checkWin();
      }
    },
    checkWin(){
      const board = this.board;
      var win = false;
      if(board[0][0] == board[0][1] && board[0][1] == board[0][2] && (board[0][0] == "X" || board[0][0] == "O")){
        win = true;
        this.currentPlayer = board[0][0];
      }else if(board[1][0] == board[1][1] && board[1][1] == board[1][2] && (board[1][0] == "X" || board[1][0] == "O")){
        win = true;
        this.currentPlayer = board[1][0];
      }else if(board[2][0] == board[2][1] && board[2][1] == board[2][2] && (board[2][0] == "X" || board[2][0] == "O")){
        win = true;
        this.currentPlayer = board[2][0];
      }else if(board[0][0] == board[1][0] && board[1][0] == board[2][0] && (board[0][0] == "X" || board[0][0] == "O")){
        win = true;
        this.currentPlayer = board[0][0];
      }else if(board[0][1] == board[1][1] && board[1][1] == board[2][1] && (board[0][1] == "X" || board[0][1] == "O")){
        win = true;
        this.currentPlayer = board[0][1];
      }else if(board[0][2] == board[1][2] && board[1][2] == board[2][2] && (board[0][2] == "X" || board[0][2] == "O")){
        win = true;
        this.currentPlayer = board[0][2];
      }else if(board[0][0] == board[1][1] && board[1][1] == board[2][2] && (board[0][0] == "X" || board[0][0] == "O")){
        win = true;
        this.currentPlayer = board[0][0];
      }else if(board[0][2] == board[1][1] && board[1][1] == board[2][0] && (board[0][2] == "X" || board[0][2] == "O")){
        win = true;
        this.currentPlayer = board[0][2];
      }
      if(win){
        this.boardSelect = [
          [true, true, true],
          [true, true, true],
          [true, true, true]
        ]
        const winner = document.querySelector(".win");
        winner.style.display = "flex";
      }
    },
    restart(){
      this.board = [
        ['', '', ''],
        ['', '', ''],
        ['', '', '']
      ];
      this.boardSelect = [
        [false, false, false],
        [false, false, false],
        [false, false, false]
      ];
      this.currentPlayer = 'X';
      const winner = document.querySelector(".win");
      winner.style.display = "none";
    }
  }
};
</script>

<style scoped>
.win{
  background-color: rgba(0, 0, 0, 0.4);
  display: flex;
  flex-direction: column;
  position: absolute;
  width: 460px;
  height: 460px;
  align-items: center;
  text-align: center;
  justify-content: center;
  z-index: 2;
}
.win p{
  font-size: 40px;
  color: aliceblue;
}
.win span{
  font-weight: bold;
  padding-bottom: 5px;
  color: #ffffff;
}
.btn{
  padding: 15px 20px;
  text-decoration: none;
  color: #fff;
  font-size: 20px;
  border: 1px solid teal;
  border-radius: 15px;
  cursor: pointer;
  font-family: 'Courier New', Courier, monospace;
  background-color: #051937;
  box-shadow: 5px 5px 5px -5px rgba(255, 255, 255, 0.6);
  transition: background 1.5s ease, box-shadow 0.5s ease-out;
}
.btn:hover{
  background: linear-gradient(4deg, #ffffff, #051937);
  box-shadow: 5px 5px 5px -5px rgba(0, 0, 0, 0.6);
  background-size: 400% 400%;
	animation: gradient 2s ease 1;
}
@keyframes gradient {
	0% {
		background-position: 50% 0%;
	}
	50% {
		background-position: 50% 100%;
	}
	100% {
		background-position: 50% 0%;
	}
}
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.game-board {
  border: 1px solid black;
  border-radius: 15px;
  display: flex;
  background: teal;
  padding: 5px;
  gap: 5px;
  flex-direction: column;
  width: fit-content;
}
.row {
  display: flex;
  flex-direction: row;
  gap: 5px;
  background: teal;
}
.cell {
  border: 1px solid black;
  background: #fff;
  border-radius: 15px;
  width: 150px;
  height: 150px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 50px;
  font-weight: bold;
}
.info{
  display: flex;
  align-items: center;
  gap: 80px;
}
.info p{
  font-size: 40px;
  color: #fff;
}
.info span{
  font-weight: bold;
  border-bottom: 2px solid #fff;
  padding-bottom: 5px;
}
</style>