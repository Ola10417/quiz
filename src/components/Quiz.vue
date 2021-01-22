<template>
    <div>
    <h2 class="mb-4">{{questionsAndAnswers[indexQuestion].question}}</h2>
    <div class="row  mx-auto">
        <button class="col me-2 py-2 h5 btn btn-outline-primary mx-auto answerbutton"  v-for="answer in questionsAndAnswers[indexQuestion].answer" :key="answer" @click="checkAnswer(answer, questionsAndAnswers[indexQuestion].id)">
        {{answer}}
        </button>
    </div>
    <br>
    <div class="row mt-3">
        <button class="w-25 mx-auto py-1 btn btn-primary" @click="home" >Wstecz</button>
    </div>
    
    
    </div>
</template>
<script>
export default {
    props: [
        'questionsAndAnswers',
        'indexQuestion'
    ],
    methods: {
        home(){
            this.$emit('home');
        },
        checkAnswer(answer, id){
            this.$emit('checkAnswer',answer,id);
        }
    }
}
</script>
<style>
.answerbutton:focus{
    background-color:#0d6efd!important;
    color: white;
}
.answerbutton:active{
    background-color:#0d6efd!important;
    color: white;
}

</style>