<template>
  <div>
    <div class="chesstable" @~click="clickInTable">
      <div class="chess" v-if="a">{{text}}</div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      text: null,
      a: false
    };
  },
  props: ["clicktime", "win"],
  methods: {
    clickInTable() {
      if (this.win === "胜负未分") {
        if (this.text !== null) {
          return;
        }
        this.a = true;
        if (this.clicktime % 2 == 0) {
          this.text = "x";
        } else {
          this.text = "o";
        }
        this.$emit("clickchess", this.text);
      }
    }
  }
};
</script>

<style>
.chesstable {
  width: 100px;
  height: 100px;
  border: 1px solid #111;
  display: flex;
  justify-content: center;
  align-items: center;
}
.chess {
  font-size: 80px;
}
</style>

