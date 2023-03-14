<template>
    <!-- Answers -->
    <div class="box_answers">
        <!-- progressBar -->
        <div class="md-stepper-horizontal orange">
            <div class="md-step active done">
                <div class="md-step-circle"><span>1</span></div>
                <div class="md-step-title">Rules</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
            <div class="md-step active done">
                <div class="md-step-circle"><span>2</span></div>
                <div class="md-step-title">Quiz</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
            <div class="md-step active done">
                <div class="md-step-circle"><span>3</span></div>
                <div class="md-step-title">Score</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
            <div class="md-step active done">
                <div class="md-step-circle"><span>4</span></div>
                <div class="md-step-title">Answers</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
        </div>
        <div class="answers_header">
            <h1>Your Right Answers</h1>
        </div>
        <div class="answers_body">
            <div  v-for="(item,index) in arrCorrectAnswers" :key='index'>
                <p class="title-question">Question</p>
                <h3>{{index+1}} - {{item.question}}</h3>
                <p class="title-correct-answer">Correct Answer</p>
                <p class="answer">{{item.answers[item.isCorrect].choix}}</p>
                <p class="title-explication">Explication</p>
                <p class="explication">{{item.explication}}</p>
                <hr>
            </div>

        </div>
        <div class="answers_footer">
            <button class="quit" @click="$emit('btn_quit')">Exit Quiz</button>
        </div>
    </div>
</template>

<script>
export default {
    props : ['arrCorrectAnswers'],
    data(){
        return{
            his_checked: false,
        }
    },
    mounted(){
        this.his_checked = true;
        console.log('d');
    }
}
</script>

<style>
.title-question,
.title-correct-answer,
.title-explication{
    padding: 12px;
    text-align: center;
    font-weight: bold;
    font-size: 22px;
}
.box_answers{
    overflow-y: scroll;
    height: 40rem;
}
</style>