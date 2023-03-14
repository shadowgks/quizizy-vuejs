<template>
    <!-- Answers -->
    <div class="box_answers">
        <div class="answers_header">
            <h1>Your Wrong Answers</h1>
        </div>
        <div class="answers_body">
            <div  v-for="(item,index) in correctAnswers" :key='index'>
                <h3>{{index+1}} - {{item.question}}</h3>
                <p class="answer">{{item.answers[item.isCorrect].choix}}</p>
                <!-- <p class="your_answer">Amazon EC2 instances can be launched on demand when needed</p> -->
                <p class="explication">{{item.explication}}</p>
                <hr>
            </div>

        </div>
        <div class="answers_footer">
            <button class="quit">Quit Quiz</button>
        </div>
    </div>
</template>

<script>
export default {
    props : ['correctAnswers'],
}
</script>

<style></style>