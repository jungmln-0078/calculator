<template>
  <div id="app">
    <h1>Calculator</h1>
    <hr>
    <input-show :inputTemp="tempStr" :inputVal="value"/>
    <input-table />
  </div>
</template>

<script>
import InputShow from './components/InputShow.vue'
import InputTable from './components/InputTable.vue'

export default {
  name: "app",
  components: { 
    InputShow,
    InputTable 
  },
  data() {
    return {
        value: 0,
        temp: 0,
        tempStr: '',
        writeTempStr: false,
        op: '',
        lastInputType: ''
    }

  },
  methods: {
    numberInput(num, type) {
      if (this.value === 0 || this.lastInputType === 'op') {
        this.value = '';
      }
      if (this.lastInputType === 'enter') {
        this.value = '';
        this.temp = '';
      }
      this.value = Number(this.value + String(num));
      this.lastInputType = type;
      if (this.writeTempStr)
        this.tempStr = this.temp + this.op + this.value;
      if (this.tempStr.includes('=')) {
        this.tempStr = '';
      }
    },
    operandInput(op, type) {
      if (this.op === '') {
        this.temp = this.value;
        this.op = op;
        this.tempStr = this.value + this.op;
        this.writeTempStr = true;
      } else {
        this.compute();
      }
      this.lastInputType = type;
    },
    compute(enter) {
      if (this.op !== '') {
        if (this.value === this.temp)
          this.tempStr = this.value + this.op + this.temp + '=';
        else
          this.tempStr += '=';
      }
      switch (this.op) {
        case '+':
          this.value += this.temp;
          break;
        case '-':
          this.value = this.temp - this.value;
          break;
        case '×':
          this.value *= this.temp;
          break;
        case '÷':
          this.value = this.temp / this.value;
          break;
        default:
          this.writeTempStr = false;
          break;
      }
      this.temp = this.value;
      this.lastInputType = 'op';
      this.op = '';
      if (enter)
        this.lastInputType = enter;
    },
    clear() {
      this.value = 0;
      this.temp = 0;
      this.tempStr = '';
      this.op = '';
      this.lastInputType = '';
      this.writeTempStr = false;
    },
    backspace() {
      if (this.op !== '' && this.temp !== 0) {
        this.temp = 0;
        this.op = '';
      } else if (this.value !== 0) {
        this.value = this.value.toString().substring(0, this.value.toString().length -1);
      }
      if (this.value === '' || this.value === '-')
        this.value = 0;
    }
  }
}

</script>

<style>
  * {
    margin: 0;
    padding: 0;
  }
  #app {
    border-spacing: 0;
    border: 1px solid black;
    border-collapse: collapse;
    width: 300px;
    height: 500px;
    margin: 0 auto;
    margin-top: 100px;
  }
  #app h1 {
    text-align: center;
    padding: 20px;
  }
  #inputshow {
    height: 60px;
    width: 100%;
  }
  #inputshow p.inputVal {
    line-height: 60px;
    text-align: right;
    font-weight: bold;
    font-size: 22px;
    margin-right: 8px;
  }
  #inputshow p.inputTemp {
    text-align: right;
    font-size: 12px;
    margin-right: 8px;
  }
  #inputTable {
    height: 350px;
    width: 100%;
  }
  #inputTable td {
    border-spacing: 0;
    border: 1px solid lightgray;
    border-collapse: collapse;
  }
  td {
    float: left;
    text-align: center;
    line-height: 68px;
    width: 72px;
    height: 68px;
    font-size: 24px;
  }
  td.colspan2 {
    width: 146px;
  }
  td.colspan3 {
    width: 220px;
  }
  a {
    display: block;
    color: black;
    text-decoration: none;
  }
  a:hover {
    background-color: lightgray;
  }
</style>
