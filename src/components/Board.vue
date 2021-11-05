<template>
  <div class="board">

    <cell
      v-for="placement, index in placements"
      :key="index"
      :placement="placement"
      @click="$emit('cell-click', { index, event: $event })"
    />
  
  </div>
</template>
<script>
import Cell from './Cell.vue'
export default {
  name: 'Board',
  components: {Cell},
  
  emits: ['cell-click'],
  props: {
    placements: Array
  }
}
</script>
<style scoped>
.board {
  padding: 0 1.2rem;
  display: grid;
  grid-template-columns: repeat(3, 4fr);
  gap: 1rem;
}
</style>
