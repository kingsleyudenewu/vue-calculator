<template>
  <div class="calculator">
    <div class="display">{{ current || '0' }}</div>
    <div @click="clear" class="btn ">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn ">%</div>
    <div @click="divide" class="btn operator">/</div>
    <div @click="append(7)" class="btn ">7</div>
    <div @click="append(8)" class="btn ">8</div>
    <div @click="append(9)" class="btn ">9</div>
    <div @click="multiply" class="btn operator">X</div>
    <div @click="append(4)" class="btn ">4</div>
    <div @click="append(5)" class="btn ">5</div>
    <div @click="append(6)" class="btn ">6</div>
    <div @click="subtract" class="btn operator">-</div>
    <div @click="append(1)" class="btn ">1</div>
    <div @click="append(2)" class="btn ">2</div>
    <div @click="append(3)" class="btn ">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append(0)" class="btn zero">0</div>
    <div @click="dot" class="btn ">.</div>
    <div class="btn ">=</div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      current: "",
      operator: null
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
    },
    append(input) {
      this.current = `${this.current}${input}`;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    },
    divide() {

    },
    multiply() {

    },
    subtract(){

    },
    add() {

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
  cursor: pointer;
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
