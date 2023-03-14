<template>
    <!-- info quiz -->
    <div class="box_info">
        <!-- progressBar -->
        <div class="half-arc" style="--percentage:25%;">
            <span class="label">25%</span>
        </div>
        <div class="info_header">
            <h2>Some Rules of this Quiz</h2>
        </div>
        <div class="info_body">
            <!-- <div class="info">1- You will have only <span>30 seconds</span> per each question.</div> -->
            <div class="info">1- Once you select your answer, you can't reselect.</div>
            <div class="info">2- You can't select any option once time goes off.</div>
            <div class="info">3- You can't exit from the Quiz while you're playing.</div>
            <div class="info">4- You'll get points on the basis of your correct answers.</div>
        </div>
        <div class="info_footer">
            <button class="quit" @click="$emit('btn_quit')">Exit Quiz</button>
            <button class="continue" @click="$emit('onBtnShowQuiz')">Continue</button>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            his_checked: false,
        }
    },
    mounted(){
        this.his_checked = true
        console.log('go');
    },
    unmounted(){
        this.his_checked = false
        console.log('out');
    }
}
</script>

<style></style>