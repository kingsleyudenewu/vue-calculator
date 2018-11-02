<template>
  <div class="calculator">
    <div class="allvalues">{{ allvalues || '0' }}</div>
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
    <div @click="equal" class="btn ">=</div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      previous: null,
      current: "",
      operator: null,
      operatorClicked: false,
      allvalues: ""
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
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.current = `${this.current}${input}`;
      this.allvalues = this.allvalues + this.current;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
      this.allvalues = this.allvalues + " / ";
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
      this.allvalues = this.allvalues + " * ";
    },
    subtract() {
      this.operator = (a, b) => b - a;
      this.setPrevious();
      this.allvalues = this.allvalues + " - ";
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
      this.allvalues = this.allvalues + " + ";
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;
      this.previous = null;
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
  /* text-align: center; */
  padding: 8px;
}
.allvalues {
  grid-column: 1 / 5;
  background-color: #c3c2c2;
  color: white;
  font-weight: bold;
  text-align: right;
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
