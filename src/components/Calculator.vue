<template>
  <div class="calculator">
    <div class="display">{{ current || '0' }}</div>
    <div @click="clear" class="btn ">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn ">%</div>
    <div class="btn operator">/</div>
    <div class="btn ">7</div>
    <div class="btn ">8</div>
    <div class="btn ">9</div>
    <div class="btn operator">X</div>
    <div class="btn ">4</div>
    <div class="btn ">5</div>
    <div class="btn ">6</div>
    <div class="btn operator">-</div>
    <div class="btn ">1</div>
    <div class="btn ">2</div>
    <div class="btn ">3</div>
    <div class="btn operator">+</div>
    <div class="btn zero">0</div>
    <div class="btn ">.</div>
    <div class="btn ">=</div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      current: "1234"
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current / 100)}`;
    }
  }
};
</script>

<style scoped>
.calculator {
  margin: 10px auto;
  max-width: 300px;
  font-size: 28px;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  display: grid;
}
.display {
  grid-column: 1 / 5;
  background-color: #333333;
  color: white;
  font-weight: bold;
  text-align: center;
  padding: 8px;
}
.zero {
  grid-column: 1 / 3;
}
.btn {
  background-color: #eeeeee;
  border: 1px solid #999999;
}
.operator {
  background-color: orange;
  color: white;
}
</style>
