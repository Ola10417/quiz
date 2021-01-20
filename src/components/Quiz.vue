<template>
    <div>
    <h2>{{questionsAndAnswers[indexQuestion].question}}</h2>
    
    <button :disabled=isDisabled v-for="answer in questionsAndAnswers[indexQuestion].answer" :key="answer" @click="checkAnswer(answer, questionsAndAnswers[indexQuestion].id)">
    {{answer}}
    </button>
    <br>
    <button @click="nextQuestion" :disabled=!isDisabled>Dalej</button>
    
    
    </div>
</template>
<script>
export default {
    props: [
        'questionsAndAnswers',
        'indexQuestion',
        'isDisabled'
    ],
    methods: {
        nextQuestion(){
            this.$emit('nextQuestion');
        },
        checkAnswer(answer, id){
            this.$emit('checkAnswer',answer,id);
        }
    }
}
</script>