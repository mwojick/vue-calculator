<template>
  <div class="calc">
    <div class="display">{{current}}</div>
    <div @click="clear" class="btn top">C</div>
    <div @click="sign" class="btn top">+/-</div>
    <div @click="percent" class="btn top">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="times" class="btn operator">x</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      prev: null,
      current: "0",
      operator: null,
      operatorClicked: false
    };
  },
  methods: {
    clear() {
      this.current = "0";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = "0";
        this.operatorClicked = false;
      }
      this.current = this.current === "0" ? number : this.current + number;
    },
    dot() {
      if (this.operatorClicked) {
        this.current = "0";
        this.operatorClicked = false;
      }
      if (this.current.indexOf(".") === -1) {
        this.current = this.current + ".";
      }
    },
    setPrev() {
      this.prev = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a, b) => b / a;
      this.setPrev();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.setPrev();
    },
    minus() {
      this.operator = (a, b) => b - a;
      this.setPrev();
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrev();
    },
    equal() {
      if (this.operator) {
        this.current = `${this.operator(
          parseFloat(this.current),
          parseFloat(this.prev)
        )}`;
        this.operator = null;
        this.prev = null;
      }
    }
  }
};
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
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
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
