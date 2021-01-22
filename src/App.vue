<template>
  <div id="app">
    <h1 class="mb-5" >QUIZ Z JĘZYKA ANGIELSKIEGO</h1>
    <div v-if="isQuizCompleted" class="mb-4">
      <h1>Wynik</h1>
    <h3>Ilość poprawnych odpowiedzi: {{points}}/6</h3>
    </div>
    <button class="btn btn-primary p-3" @click="startQuiz" v-if="!isQuizStarted">{{buttonTitle}}</button>
    
    <Quiz class="row w-50 mx-auto" v-if="isQuizStarted" :isDisabled=isDisabled :questionsAndAnswers=questionsAndAnswers :indexQuestion=indexQuestion @home="gohome" @checkAnswer="checkA"/>
    
    
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
      isQuizCompleted:false,
      indexQuestion:0,
      points:0,
      buttonTitle:'Rozpocznij quiz',
      questionsAndAnswers:[
        {id:1, question:'... sofa do you like better; the black or the white one?', answer:['Which', 'What', 'Who']},
        {id:2, question:'Are you enjoying ...?', answer:['your', 'yourselves', 'you']},
        {id:3, question:'What would you like to have for ... lunch today?', answer:['a', 'the', '-']},
        {id:4, question:'Let ... do whatever I want.', answer:['I', 'me', 'my']},
        {id:5, question:'I ... France twice in my life.', answer:['have been in', 'have been to', 'went to']},
        {id:6, question:'If the police had not caught him, he ... in prison now.', answer:['will not be', 'would not have been', 'would not be']},
        {id:7, question:'We will be late ... we leave now.', answer:['provided', 'in case', 'unless']},
        {id:8, question:'Let\'s go swimming, ...?', answer:['shall we', 'should we', 'let\'s not']},
        {id:9, question:'I ... to think what will happen if the boss finds out.', answer:['care', 'resist', 'dread']},
        {id:10, question:'I ... here for ten years in June next year.', answer:['will live', 'will be living', 'will have been living']},
        {id:11, question:'How can you be so indifferent ... the suffering of others?', answer:['to', 'about', 'towards']},
      ],
      correctAnswers:['Which', 'yourselves', '-', 'me', 'have been to','would not be', 'unless', 'shall we', 'dread', 'will have been living', 'to']
    }
  },
  methods:{
    shuffle() {
      var currentIndex = this.questionsAndAnswers.length, temporaryValue, randomIndex;
      while (0 !== currentIndex) {
        randomIndex = Math.floor(Math.random() * currentIndex);
        currentIndex -= 1;
        temporaryValue = this.questionsAndAnswers[currentIndex];
        this.questionsAndAnswers[currentIndex] = this.questionsAndAnswers[randomIndex];
        this.questionsAndAnswers[randomIndex] = temporaryValue;
        }
      },
      gohome()
      {
        this.isQuizStarted=false
        this.points=0
      },
    startQuiz()
    {
      this.shuffle()
      this.isQuizStarted=true
      this.points=0
      this.isQuizCompleted=false
      this.buttonTitle='Rozpocznij quiz'
    },
    nextQ(){
      if(this.indexQuestion<=5)
      {
        this.indexQuestion++
      }
      if(this.indexQuestion==6)
      {
        this.isQuizStarted=false
        this.indexQuestion=0
        this.isQuizCompleted=true
        this.buttonTitle='Powtórz quiz'
      }
      this.isDisabled=false
      
    },
    checkA(answer, id){
      if(answer==this.correctAnswers[id-1])
      {
        this.points++
      }
      this.isDisabled=true
      this.nextQ()
      
    }
  },
  computed:{
    

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
  margin-top: 70px;
}
</style>
