<template>
  <div id="app">
    <game-board>

    </game-board>
  </div>
</template>

<script>
import GameBoard from './components/GameBoard.vue';

export default {
  components: {
    GameBoard
  }
};
</script>
<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app{
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  gap: 50px;
  align-items: center;
  justify-content: center;
  background: linear-gradient(to right top, #051937, #004d7a, #008793, #00bf72, #a8eb12);
}
</style>