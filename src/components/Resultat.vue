<template>
    <!-- resultat -->
    <div class="box_resultat">
        <div class="half-arc" style="--percentage:75%;">
  <span class="label">75%</span>
</div>
        <div class="container">
            <input type="radio" class="radio" name="progress" value="seventyfive" id="seventyfive" :checked="his_checked">

            <div class="progress">
                <div class="progress-bar"></div>
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