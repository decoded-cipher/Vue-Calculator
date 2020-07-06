<template>
  <div class="calculator">
    
    <div class="display"> 498467414</div>

    <div class="operator">C</div>
    <div class="operator">+/-</div>
    <div class="operator">%</div>
    <div class="operator">÷</div>
    
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="operator">x</div>
    
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="operator">-</div>
    
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="operator">+</div>
    
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="operator">=</div>

  </div>
</template>

<script>
  export default {

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