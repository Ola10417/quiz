<template>
  <div id="app">
    <h1>QUIZ Z JĘZYKA ANGIELSKIEGO</h1>
    <button @click="startQuiz" v-if="!isQuizStarted">Zacznij quiz</button>
    <Quiz v-if="isQuizStarted" :isDisabled=isDisabled :questionsAndAnswers=questionsAndAnswers :indexQuestion=indexQuestion @nextQuestion="nextQ" @checkAnswer="checkA"/>
    <h3>Ilość poprawnych odpowiedzi: {{points}}/6</h3>
    
  </div>
</template>

<script>
import Quiz from './components/Quiz.vue';
export default {
  components:{
    Quiz,
  },
  name: 'App',
  data(){
    return{
      isQuizStarted:false,
      indexQuestion:0,
      points:0,
      isDisabled:false,
      questionsAndAnswers:[
        {id:1, question:'... sofa do you like better; the black or the white one?', answer:['Which', 'What', 'Who']},
        {id:2, question:'Are you enjoying ...?', answer:['your', 'yourselves', 'you']},
        {id:3, question:'What would you like to have for ... lunch today?', answer:['a', 'the', '-']},
        {id:4, question:'Let ... do whatever I want.', answer:['I', 'me', 'my']},
        {id:5, question:'I ... France twice in my life.', answer:['have been in', 'have been to', 'went to']},
        {id:6, question:'If the police had not caught him, he ... in prison now.', answer:['will not be', 'would not have been', 'would not be']},
      ],
      correctAnswers:['Which', 'yourselves', '-', 'me', 'have been to','would not be',]
    }
  },
  methods:{
    startQuiz()
    {
      this.isQuizStarted=true
      this.points=0
    },
    nextQ(){
      if(this.indexQuestion<5)
      {
        this.indexQuestion++
      }
      if(this.indexQuestion==5)
      {
        this.isQuizStarted=false
        this.indexQuestion=0
      }
      this.isDisabled=false
      
    },
    checkA(answer){
      if(answer==this.correctAnswers[this.indexQuestion])
      {
        this.points++
      }
      this.isDisabled=true
      
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
}
</style>
