<template>
  <div :class="['cell', {'placement-x': placement === 'X', 'placement-o': placement === 'O'}]" @click="$emit('click', $event)">
    {{ placement || '&nbsp;' }}
  </div>
</template>
<script>
export default {
  name: 'Cell',
  components: {},

  emits: ['click'],
  props: {
    placement: String
  }
}
</script>
<style scoped>
  .cell {
    border: 1px solid black;
    font-size: 4rem;
    line-height: 6rem;
  }

  .placement-x {
    color: red;
  }

  .placement-o {
    color: teal;
  }
</style>
