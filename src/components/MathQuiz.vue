<template>
    <div> 
        <div v-if="isQuizStarted"> 
            <h4>{{leftOperand}} {{operator}} {{rightOperand}} </h4>
            <div v-for="(ans,index) in answers" :key="index">
                <button @click="submitAnswer(ans)"> {{ans}} </button>
            </div>
        </div>
        <div>
            <button  v-if="!isQuizStarted" @click="startQuiz"> start </button>
            <button  @click="$emit('onBack')"> Back </button>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        operator:{
            type: String,
            default: null,
        }
    },
    data(){
        return {  
            leftOperand: null,
            rightOperand: null,
            isQuizStarted: false,
            answers: [],
            methods: {
                '+' : (a,b) => a+b,
                '-' : (a,b) => a-b,
                '*' : (a,b) => a*b,
                '/' : (a,b) => a/b,
            },
            expectedAnswer: null,
        }
    },
    methods:{
        submitAnswer(selectedAnswer){
            if(selectedAnswer !== this.expectedAnswer){
                alert("WRONG ANSWER");
            }
            this.startQuiz();
        },
        startQuiz(){
            this.isQuizStarted = true;
            this.leftOperand = parseInt(Math.random() *13);
            this.rightOperand = parseInt(Math.random() *13);
            this.answers = [];
            const methodToUse = this.methods[this.operator];
            for(let i = 0; i < 5;i++){
                const answer = methodToUse(this.leftOperand+parseInt(Math.random()*3),this.rightOperand+parseInt(Math.random()*3));
                this.answers.push(answer);
            }
            this.expectedAnswer = methodToUse(this.leftOperand,this.rightOperand);
            this.answers[parseInt(Math.random()*this.answers.length)] = this.expectedAnswer;
        }
    }
}
</script>
