<template>
  <h1>Tic Tac Toe</h1>
  <p>Round: {{ gameState.turnCount }}</p>
  <score-board :scorePlayerX="gameState.scorePlayerX" :scorePlayerO="gameState.scorePlayerO"/>
  <board
    :placements="gameState.placements"
    @cell-click="onCellClick"
  />

</template>

<script>
import { reactive } from '@vue/reactivity'
import Board from './components/Board.vue'
import ScoreBoard from './components/ScoreBoard.vue'

export default {
  name: 'App',
  components: {Board, ScoreBoard},

  setup() {
    const gameState = reactive({
      scorePlayerX: 0,
      scorePlayerO: 0,
      turnCount: 0,
      placements: [null, null, null, null, null, null, null, null, null],
    })

    const hasMatch = placement => {

      for (let row = 0; row < 3; row++) {
        if (gameState.placements[3 * row] === placement
          && gameState.placements[3 * row + 1] === placement
          && gameState.placements[3 * row + 2] === placement) {
          return true
        }
      }

      for (let column = 0; column < 3; column++) {
        if (gameState.placements[column] === placement
          && gameState.placements[column + 3] === placement
          && gameState.placements[column + 6] === placement) {
          return true
        }
      }

      if (gameState.placements[0] === placement && gameState.placements[4] === placement && gameState.placements[8]
        || gameState.placements[2] === placement && gameState.placements[4] === placement && gameState.placements[6]) {
          return true
      }

      return false
    }

    return {
      gameState,

      onCellClick: ({ index }) => {

        if (gameState.placements[index] !== null) {
          return
        }

        const playerIndex = gameState.turnCount % 2
        const placement = playerIndex === 0 ? 'X' : 'O'
        
        gameState.placements[index] = placement
        gameState.turnCount++


        if (hasMatch(placement)) {
          
          if (placement === 'X') {
            gameState.scorePlayerX++
          } else {
            gameState.scorePlayerO++
          }

          gameState.turnCount = 0
          gameState.placements.fill(null)
        } else if (gameState.turnCount >= 9) {

          gameState.turnCount = 0
          gameState.placements.fill(null)
        }
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
