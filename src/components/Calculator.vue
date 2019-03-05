<template>
  <div class="calculator-app">
    <div class="calculator">
      <div class="display">{{currunt || '0'}}</div>
      <div @click="clear" class="btn">C</div>
      <div @click="sign" class="btn">+/-</div>
      <div @click="percent" class="btn">%</div>
      <div @click="devide" class="btn operator">&divide;</div>
      <div @click="append('7')" class="btn">7</div>
      <div @click="append('8')" class="btn">8</div>
      <div @click="append('9')" class="btn">9</div>
      <div @click="times" class="btn operator">&times;</div>
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

    <div class="ref">
      <p>Created with help of freeCodeCamp.org's 'Build a Calculator with Vue.js' video</p>
      <a href="https://www.youtube.com/watch?v=m1_ih43p24s&t=167s">https://www.youtube.com/watch?v=m1_ih43p24s&t=167s</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data() {
    return {
      previous: null,
      currunt: '',
      operator: null,
      operatorClicked: false,
    }
  },
  methods: {
    clear() {
      this.currunt = '';
    },
    sign() {
      this.currunt = this.currunt.charAt(0) === '-' ? this.currunt.slice(1) : `-${this.currunt}`;
    },
    percent() {
      this.currunt = `${parseFloat(this.currunt) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.currunt = '';
        this.operatorClicked = false;
      }

      this.currunt = `${this.currunt}${number}`;
    },
    dot() {
      if (this.currunt.indexOf('.') === -1) {
        // dot dosn't exists
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.currunt;
      this.operatorClicked = true;
    },
    devide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    times() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equal() {
      this.currunt = `${this.operator(parseFloat(this.currunt), parseFloat(this.previous))}`;

      this.previous = null;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.calculator {
  max-width: 400px;
  margin: 0 auto;
  display: grid;
  font-size: 32px;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  background-color: #333;
  color: #fff;
  grid-column: 1 / 5;
}

.btn {
  background-color: #eee;
  border: 1px solid;
}

.zero {
  grid-column: 1 / 3;
}

.operator {
  background-color: orange;
  color: #fff;
}
</style>
