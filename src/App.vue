<template>
  <div id="app">
    <math-quiz v-if="selectedOperator" :operator="selectedOperator" @onBack="resetOperator"/>
    <select-operator v-if="!selectedOperator" @changeOperator="changeOperator" />
    <h1> {{selectedOperator}} </h1>
  </div>
</template>

<script>
import SelectOperator from './components/OperatorSelector.vue';
import MathQuiz from './components/MathQuiz.vue';
export default {
  name: 'App',
  components: {
    SelectOperator,
    MathQuiz
  },
  data(){
    return {
      selectedOperator: null,
    }
  },
  methods:{
    changeOperator(operator){
      this.selectedOperator = operator;
    },
    resetOperator(){
      this.selectedOperator = null;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 24px;
}
</style>
