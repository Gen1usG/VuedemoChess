<template>
    <div class="container">
      <div>
        <div class="wrapper">
          <Cell @clickchess="changeN(0,$event)" :clicktime="n" :win="winner"></Cell>
          <Cell @clickchess="changeN(1,$event)" :clicktime="n" :win="winner"></Cell>
          <Cell @clickchess="changeN(2,$event)" :clicktime="n" :win="winner"></Cell>
        </div>
        <div class="wrapper">
          <Cell @clickchess="changeN(3,$event)" :clicktime="n" :win="winner"></Cell>
          <Cell @clickchess="changeN(4,$event)" :clicktime="n" :win="winner"></Cell>
          <Cell @clickchess="changeN(5,$event)" :clicktime="n" :win="winner"></Cell>
        </div>
        <div class="wrapper">
          <Cell @clickchess="changeN(6,$event)" :clicktime="n" :win="winner"></Cell>
          <Cell @clickchess="changeN(7,$event)" :clicktime="n" :win="winner"></Cell>
          <Cell @clickchess="changeN(8,$event)" :clicktime="n" :win="winner"></Cell>
        </div>
      </div>
      <div>{{winner}}</div>
    </div>
    
 
</template>

<script>
import Cell from "./components/cell";

export default {
  name: "app",
  components: {
    Cell
  },
  data() {
    return {
      n: 0,
      result: [[null, null, null], [null, null, null], [null, null, null]],
      winner: "胜负未分"
    };
  },
  methods: {
    changeN(id, chess) {
      if (this.winner === "胜负未分") {
        this.n++;
        this.result[Math.floor(id / 3)][id % 3] = chess;
        this.judege();
      }
    },

    judege() {
      for (let i = 0; i <= 2; i++) {
        if (
          this.result[i][0] != null &&
          this.result[i][0] == this.result[i][1] &&
          this.result[i][1] == this.result[i][2]
        ) {
          this.winner = `${this.result[i][0]}'胜利'`;
        }
      }
      for (let j = 0; j <= 2; j++) {
        if (
          this.result[0][j] != null &&
          this.result[0][j] == this.result[1][j] &&
          this.result[1][j] == this.result[2][j]
        ) {
          this.winner = `${this.result[0][j]}'胜利'`;
        }
      }
      if (
        this.result[0][0] == this.result[1][1] &&
        this.result[0][0] == this.result[2][2] &&
        this.result[0][0] != null
      ) {
        this.winner = `${this.result[0][0]}'胜利'`;
      } else if (
        this.result[0][2] == this.result[1][1] &&
        this.result[0][2] == this.result[2][0] &&
        this.result[0][2] != null
      ) {
        this.winner = `${this.result[0][2]}'胜利'`;
      }
    }
  }
};
</script>

<style>
.wrapper {
  display: flex;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column;
}
</style>
