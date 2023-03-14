<template>
    <!-- quiz -->
    <div class="box_quiz">
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
}
</script>

<style></style>