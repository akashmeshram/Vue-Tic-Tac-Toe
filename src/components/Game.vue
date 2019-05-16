<template>
  <div class="game">
        <div class="game-board">
          <Board />
        </div>
        <div class="game-info">
          <div></div>
          <ol></ol>
        </div>
    </div>
</template>

<script>

import Board from './Board.vue'

export default {
  name: 'Game',
  components: {
    Board
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
