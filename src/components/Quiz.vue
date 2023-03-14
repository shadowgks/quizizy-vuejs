<template>
    <!-- quiz -->
    <div class="box_quiz">
        <!-- progressBar -->
        <div class="md-stepper-horizontal orange">
            <div class="md-step active done">
                <div class="md-step-circle done"><span>1</span></div>
                <div class="md-step-title">Rules</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
            <div class="md-step active editable">
                <div class="md-step-circle"><span>2</span></div>
                <div class="md-step-title">Quiz</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
            <div class="md-step">
                <div class="md-step-circle"><span>3</span></div>
                <div class="md-step-title">Score</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
            <div class="md-step">
                <div class="md-step-circle"><span>4</span></div>
                <div class="md-step-title">Answers</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
        </div>
        <div class="quiz_header">
            <h3>Quiz of AWS</h3>
            <!-- <div class="time">
                <span class="text_time">Time left</span>
                <span class="count">30</span>
            </div> -->
        </div>
        <div class="quiz_body">
            <div class="title">
                <h2>{{currentIndex+1}} - {{questions.question}}</h2>
            </div>
            <div class="questions">
                <div>
                    <div 
                    class="question" 
                    @click="$emit('onAnswerSelected', index)" 
                    v-for="(answer, index) in questions.answers" 
                    :key="index" 
                    :class="{'correct'   : questions.selected != null && index == questions.isCorrect},
                            {'incorrect' : questions.selected != questions.isCorrect && index == questions.selected}
                    ">
                        <p>{{answer.choix}}</p>
                        <i v-if="questions.selected !== null && index === questions.isCorrect" 
                        class="fa-regular fa-circle-check good"></i>
                        <i v-if="questions.selected != questions.isCorrect && index == questions.selected" 
                        class="fa-regular fa-circle-xmark faild"></i>
                    </div>
                </div>
            </div>
        </div>
        <div class="quiz_footer">
            <p><span class="step">{{currentIndex+1}}</span> of <span class="all">{{lenght_data}}</span> Questions</p>
            <div>
                <button 
                class="next" 
                v-show="questions.selected != null" 
                @click="$emit('onNextQuestion')">Next</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props : ['questions','currentIndex','lenght_data'],
    data(){
        return{
            his_checked: false,
        }
    },
    mounted(){
        this.his_checked = true
        console.log('quiz');
    },
}
</script>

<style scoped>
.box_quiz{
    overflow-y: scroll;
    height: 40rem;
}
</style>