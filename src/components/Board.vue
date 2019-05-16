<template>
  <div>
        <div class="status">{{msg}}</div>
        <div class="board-row">
          <Square v-bind:Value="squares[0]"  @onClick="handleClick(0)"/>
          <Square v-bind:Value="squares[1]"  @onClick="handleClick(1)"/>
          <Square v-bind:Value="squares[2]"  @onClick="handleClick(2)"/>
        </div>
        <div class="board-row">
          <Square v-bind:Value="squares[3]"  @onClick="handleClick(3)"/>
          <Square v-bind:Value="squares[4]"  @onClick="handleClick(4)"/>
          <Square v-bind:Value="squares[5]"  @onClick="handleClick(5)"/>
        </div>
        <div class="board-row">
          <Square v-bind:Value="squares[6]"  @onClick="handleClick(6)"/>
          <Square v-bind:Value="squares[7]"  @onClick="handleClick(7)"/>
          <Square v-bind:Value="squares[8]"  @onClick="handleClick(8)"/>
        </div>
      </div>
</template>

<script>

import Square from './Square.vue'

export default {
  name: 'Board',
  data: function () {
    return {
      squares: Array(9).fill(null),
      xIsNext: true,
      status: true
    }
  },
  components: {
    Square
  },  
  methods: {
      handleClick: function(num) {
          if(!this.status || this.squares[num]) {
            return;
          }
          Vue.set(this.squares, num, this.xIsNext ? 'X' : 'O');
          this.xIsNext = !this.xIsNext;
      },
      claculateWinner: function() {
          const lines = [
            [0, 1, 2],
            [3, 4, 5],
            [6, 7, 8],
            [0, 3, 6],
            [1, 4, 7],
            [2, 5, 8],
            [0, 4, 8],
            [2, 4, 6],
          ];
          for (let i = 0; i < lines.length; i++) {
            const [a, b, c] = lines[i];
            if (this.squares[a] && this.squares[a] === this.squares[b] && this.squares[a] === this.squares[c]) {
              this.status = false;
              return this.squares[a];
            }
          }
          return null;
      }
  },
  computed: {
    msg: function() {
      var winner = this.claculateWinner();
      if(winner) {
        return 'Winner: ' + winner;
      } else {
        return 'Next player: ' + (this.xIsNext ? 'X' : 'O');
      }      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
