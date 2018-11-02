<template>
  <div class="calculator">
    <div class="display">{{ current }}</div>
    <div class="btn ">C</div>
    <div class="btn">+/-</div>
    <div class="btn ">%</div>
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

  data: () =>{
    return{
      current: ''
    }

  }

}
</script>

<style scoped>
  .calculator{
    margin: 10px auto;
    max-width: 300px;
    font-size: 28px;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    display: grid;
  }
  .display{
    grid-column: 1 / 5;
    background-color: #333333;
    color: white;
    font-weight: bold;
    text-align: center;
  }
  .zero{
    grid-column: 1 / 3;
  }
  .btn{
    background-color: #eeeeee;
    border: 1px solid #999999;
  }
  .operator{
    background-color: orange;
    color: white;
  }
</style>
