<script>
    // import data from "../assets/js/data/newData.json";
export default {
    props : ['questions','currentIndex','lenght_data'],

    data(){
        return{
            score : 0,
        }
    },
    methods: {
        choseAnswer(e){
            console.log(e);
        }
    },
}
</script>

<template>
    <!-- quiz -->
    <div class="box_quiz">
        <!-- {{myJson[4]['question']}} -->
        <div class="quiz_header">
            <h3>Quiz of AWS</h3>
            <div class="time">
                <span class="text_time">Time left</span>
                <span class="count">30</span>
            </div>
        </div>
        <div class="quiz_body">
            <div class="title">
                <h2>{{questions.question}}</h2>
            </div>
            <div class="questions">
                <div>
                    <!-- correct || class 
                    <i class="fa-regular fa-circle-check good"></i>
                    --> 
                    <!-- incorrect || class 
                    <i class="fa-regular fa-circle-xmark faild"></i>
                    --> 
                    <div 
                    class="question" 
                    v-on:click="$emit('onAnswerSelected', answer.isCorrect)" 
                    v-for="(answer, index) in questions.answers" 
                    :key="index" 
                    @click="choseAnswer(questions.isCorrect)"
                    :class="{'correct' : questions.selected != null && answer.isCorrect == true},
                    {'incorrect' : questions.selected != true && answer.isCorrect == questions.selected}">
                        <p>{{answer.choix}}</p>
                        <!-- {{answer.isCorrect}} -->
                    </div>
                    <!-- <div class="question incorrect">
                        <p>Users retain full administrative access to their Amazon EC2 instances.</p><i class="fa-regular fa-circle-xmark faild"></i>
                    </div>
                    <div class="question">
                        <p>Amazon EC2 instances can be launched on demand when needed.</p>
                    </div>
                    <div class="question">
                        <p>Users can permanently run enough instances to handle peak workloads.</p>
                    </div> -->
                </div>
            </div>
        </div>
        <div class="quiz_footer">
            <p><span class="step">{{currentIndex+1}}</span> of <span class="all">{{lenght_data}}</span> Questions</p>
            <div>
                <!-- <button class="submit">Submit</button> -->
                <button v-show="questions.selected != null" class="next" @click="index_answer++">Next</button>
            </div>
        </div>
    </div>
</template>

<style></style>