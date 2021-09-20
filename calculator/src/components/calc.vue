<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="main">
      <input type="number" v-model.number="operand1" />
      <input type="number" v-model.number="operand2" />
      ={{ result }}
    </div>
    <br />
    <button @click='add(operand1, operand2)'>+</button>
    <button @click='sub(operand1, operand2)'>-</button>
    <button @click='mult(operand1, operand2)'>*</button>
    <button @click='div(operand1, operand2)'>/</button>
    <button @click='pow(operand1, operand2)'>**</button>
    <button @click='mod(operand1, operand2)'>%</button>
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
      error: 'На ноль делить незя!'
    }
  },
  methods: {
    add (operand1, operand2) {
      this.result = operand1 + operand2
    },
    sub (operand1, operand2) {
      this.result = operand1 - operand2
    },
    mult (operand1, operand2) {
      this.result = operand1 * operand2
    },
    div (operand1, operand2) {
      if (operand1 === 0 || operand2 === 0) {
        this.result = this.error
      } else {
        this.result = operand1 / operand2
      }
    },
    pow (operand1, operand2) {
      this.result = operand1 ** operand2
    },
    mod (operand1, operand2) {
      this.result = operand1 % operand2
    }
  }
}
</script>
