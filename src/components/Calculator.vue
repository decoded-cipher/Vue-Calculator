<template>
  <div class="calculator">

    <div class="display">{{ current || 0 }}</div>

    <div @click="clear" class="operator">C</div>
    <div @click="sign" class="operator">+/-</div>
    <div @click="percentage" class="operator">%</div>
    <div @click="divide" class="operator">÷</div>

    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="multiply" class="operator">x</div>

    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="subtract" class="operator">-</div>

    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="operator">+</div>

    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="operator">=</div>

  </div>
</template>

<script>
  export default {
    data() {
      return {
        previous: null,
        current: '',
        operator: null,
        operatorClicked: false
      }
    },
    methods: {
      clear() {
        this.current = '';
      },
      sign() {
        this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`;
      },
      percentage() {
        this.current = `${parseFloat(this.current) / 100}`;
      },
      append(number) {
        if (this.operatorClicked) {
          this.current = '';
          this.operatorClicked = false;
        }
        this.current = `${this.current}${number}`;
      },
      dot() {
        if (this.current.indexOf('.') === -1) {
          this.append('.');
        }
      },
      setPrevious() {
        this.previous = this.current;
        this.operatorClicked = true;
      },
      divide() {
        this.operator = (a, b) => a / b;
        this.setPrevious();
      },
      multiply() {
        this.operator = (a, b) => a * b;
        this.setPrevious();
      },
      subtract() {
        this.operator = (a, b) => a - b;
        this.setPrevious();
      },
      add() {
        this.operator = (a, b) => a + b;
        this.setPrevious();
      },
      equal() {
        this.current = `${this.operator(
          parseFloat(this.current), 
          parseFloat(this.previous)
          )}`;
        this.previous = null;
      }
    }
  }
</script>

<style scoped>
  .calculator {
    margin: auto;
    width: 600px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    /* grid-auto-rows: minmax(50px, auto); */
  }

  .display {
    grid-column: 1 /5;
    padding: 30px;
    font-weight: 600;
    font-size: 45px;
    background-color: #484848;
    color: white;
  }

  .zero {
    grid-column: 1 / 3;
  }

  .btn {
    cursor: pointer;
    background-color: #3a3737;
    padding: 15px;
    color: white;
    font-size: 30px;
    font-weight: 600;
    border: gray 1px solid;
  }

  .btn:hover {
    background-color: gray;
    color: white;
  }

  .operator {
    cursor: pointer;
    background-color: #484848;
    color: white;
    padding: 15px;
    font-size: 30px;
    font-weight: 400;
    border: gray 1px solid;
  }

  .operator:hover {
    background-color: gray;
    color: white;
  }

  @media only screen and (max-width: 768px) {
    .calculator {
      display: grid;
      width: 330px;
      grid-template-columns: repeat(4, 1fr);
    }

    .display {
      grid-column: 1 /5;
      font-weight: 600;
      font-size: 30px;
      background-color: #484848;
      color: white;
    }

    .zero {
      grid-column: 1 / 3;
    }

    .btn {
      background-color: #3a3737;
      color: white;
      font-size: 20px;
      font-weight: 600;
      border: gray 1px solid;
    }

    .btn:hover {
      background-color: gray;
      color: white;
    }

    .operator {
      background-color: #484848;
      color: white;
      font-size: 20px;
      font-weight: 400;
      border: gray 1px solid;
    }

    .operator:hover {
      background-color: gray;
      color: white;
    }
  }
</style>