<template>
  <div class="calc">
    <div class="display">0</div>
    <div class="btn top">C</div>
    <div class="btn top">+/-</div>
    <div class="btn top">%</div>
    <div class="btn operator">÷</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator">x</div>
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">-</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">+</div>
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
</template>

<script>
export default {};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calc {
  border: 0.5px solid rgb(146, 146, 146);
  font-size: 26px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  width: 300px;
}

.display {
  border: 0.5px solid rgb(146, 146, 146);
  font-size: 38px;
  grid-column: 1/5;
  background-color: black;
  color: white;
}

.zero {
  grid-column: 1/3;
}

.btn {
  background-color: #eee;
  border: 0.5px solid rgb(146, 146, 146);
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.btn:hover {
  background-color: white;
}

.operator {
  background-color: rgb(255, 167, 5);
  color: white;
}

.operator:hover {
  background-color: rgb(194, 126, 0);
}
.top {
  background-color: rgb(209, 209, 209);
}
</style>
