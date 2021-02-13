<template>
    <div>
        <button @click="changeOperator('+')">Addition <br> +</button>
        <button @click="changeOperator('-')"> Subtraction <br> -</button>
        <button @click="changeOperator('/')">Division <br> /</button>
        <button @click="changeOperator('*')">Multiplication <br> *</button>
    </div>
</template>
<script>
export default {
    methods:{
        changeOperator(operator){
            this.$emit('changeOperator',operator);
        }
    }
}
</script>
<style>
button {
  background-color: #4CAF50; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 10px;
}
</style>
