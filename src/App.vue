<template>
  <div id="app">
    <h1>QUIZ Z JĘZYKA ANGIELSKIEGO</h1>
    <button @click="startQuiz" v-if="!isQuizStarted">Zacznij quiz</button>
    <Quiz v-if="isQuizStarted" :questionsAndAnswers=questionsAndAnswers :indexQuestion=indexQuestion @nextQuestion="nextQ"/>
   
    
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
      questionsAndAnswers:[
        {id:1, question:'... sofa do you like better; the black or the white one?', answerA:'Which', answerB:'What', answerC:'Who'},
        {id:2, question:'Are you enjoying ...?', answerA:'your', answerB:'yourselves', answerC:'you'},
        {id:3, question:'What would you like to have for ... lunch today?', answerA:'a', answerB:'the', answerC:'-'},
        {id:4, question:'Let ... do whatever I want.', answerA:'I', answerB:'me', answerC:'my'},
        {id:5, question:'I ... France twice in my life.', answerA:'have been in', answerB:'have been to', answerC:'went to'},
        {id:6, question:'If the police had not caught him, he ... in prison now.', answerA:'will not be', answerB:'would not have been', answerC:'would not be'},
      ],
      correctAnswers:['Which', 'yourselves', '-', 'me', 'have been to','would not be',]
    }
  },
  methods:{
    startQuiz()
    {
      this.isQuizStarted=true
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
