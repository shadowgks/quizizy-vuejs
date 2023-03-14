<template>
    <!-- resultat -->
    <!-- resultat -->
    <div class="box_resultat">
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
            <div class="md-step">
                <div class="md-step-circle"><span>4</span></div>
                <div class="md-step-title">Answers</div>
                <div class="md-step-bar-left"></div>
                <div class="md-step-bar-right"></div>
            </div>
        </div>
        <div class="resultat_header">
            <i class="fa-solid fa-ranking-star"></i>
        </div>
        <div class="resultat_body">
            <!-- <div class="name_user">
                <h4>saad</h4>
            </div> -->
            <div class="text_finish">
                <span>Completed the Quiz!</span>
            </div>
            <div class="score">
                <p>You got <span>{{score}}</span> out of <span>{{lenght_data}}</span></p>
            </div>
        </div>
        <div class="resultat_footer">
            <button class="quit" @click="$emit('btn_quit')">Quit Quiz</button>
            <button class="continue" @click="$emit('onBtnShowAnswers')">Your Ansewers</button>
        </div>
    </div>
</template>

<script>
export default {
    props : ['lenght_data','score'],
    data(){
        return{
            his_checked: false,
        }
    },
    mounted(){
        this.his_checked = true;
    }
}
</script>

<style></style>