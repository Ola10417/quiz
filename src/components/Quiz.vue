<template>
    <div>
    <h2>{{questionsAndAnswers[indexQuestion].question}}</h2>
    <button>{{questionsAndAnswers[indexQuestion].answerA}}</button>
    <button>{{questionsAndAnswers[indexQuestion].answerB}}</button>
    <button>{{questionsAndAnswers[indexQuestion].answerC}}</button>
    <br>
    <button @click="nextQuestion">Dalej</button>
    
    <h3>Ilość poprawnych odpowiedzi: 0/6</h3>
    </div>
</template>
<script>
export default {
    props: [
        'questionsAndAnswers',
        'indexQuestion'
    ],
    methods: {
        nextQuestion(){
            this.$emit('nextQuestion');
        }
    }
}
</script>