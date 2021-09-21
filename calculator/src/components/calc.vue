<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="main">
      <input type="number" v-model.number="operand1" :disabled='activ' />
      <input type="number" v-model.number="operand2" />
      ={{ result }}
    </div>
    <div class="error" v-if='error'>
      {{ error }}
    </div>
    <div class="opirations" >
      <button v-for='operator in operators'
        @click='calculate(operator)'
        :key='operator'
        :title='operator'
        :disabled="operand1 === '' || operand2 === ''">
        {{ operator }}
      </button>
    </div>
    <div class="check">
      <input type="checkbox" id='keyboard' v-model='show' />
      <label for="keyboard">Отобразить экранную клавиатуру</label>
    </div>
    <div class="keyboard" v-show='show'>
      <button v-for='key in keys'
      :key='key'>{{ key }}</button>
    </div>
    <div class="checkInput">
      <input type="radio" id='operand#1' :value='false' name='input' v-mode.="act"/>
      <label for="operand#1">Операнд 1</label>
      {{act}}
      <input type="radio" id='operand#2' :value='true' name='input' v-mode="act"/>
      <label for="operand#2">Операнд 2</label>
      {{act}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'calc',
  props: {
    msg: String
  },
  data () {
    return {
      operand1: 0,
      operand2: 0,
      result: 0,
      error: '',
      operators: ['+', '-', '*', '/', '**', '%'],
      keys: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'Del'],
      show: false,
      activ: true,
      act: ''
    }
  },
  methods: {
    calculate (operator = '+') {
      this.error = ''
      switch (operator) {
        case '+':
          this.add()
          break
        case '-':
          this.sub()
          break
        case '*':
          this.mult()
          break
        case '/':
          this.div()
          break
        case '**':
          this.pow()
          break
        case '%':
          this.mod()
          break
      }
    },
    add () {
      this.result = this.operand1 + this.operand2
    },
    sub () {
      this.result = this.operand1 - this.operand2
    },
    mult () {
      this.result = this.operand1 * this.operand2
    },
    div () {
      if (this.operand2 === 0) {
        this.error = 'На ноль делить незя!!!'
      } else {
        this.result = this.operand1 / this.operand2
      }
    },
    pow () {
      this.result = this.operand1 ** this.operand2
    },
    mod () {
      this.result = this.operand1 % this.operand2
    }
  }
}
</script>
