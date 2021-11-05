<template>
  <div class="score-board">
    <div class="column">
      <div class="player player-x">X</div>
      <div class="score">{{ scorePlayerX }}</div>
      
    </div>
    <div class="column">
      :
    </div>
    <div class="column">
      <div class="player player-y">O</div>
      <div class="score">{{ scorePlayerO }}</div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'ScoreBoard',
  components: {},

  props: {
    scorePlayerX: Number,
    scorePlayerO: Number,
  }
}
</script>
<style scoped>

  .score-board {
    display: grid;
    grid-template-columns: 4fr 4fr 4fr;
    padding: 1.2rem;
    gap: 1rem;
  }

  .column {
    padding: 1.2rem;
  }

  .player-x {
    color: red;
  }

  .player-y {
    color: teal;
  }

  .player {
    font-size: 2rem;
  }

  .score {
    font-size: 3rem;
  }
</style>
