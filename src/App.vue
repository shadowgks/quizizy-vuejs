<template>
  <main>
    <!-- Background image -->
    <div class="bg_image"></div>
    <Quiz 
    :questions="myJson[current_question]" 
    :currentIndex="current_question" 
    :lenght_data="myJson.length" 
    @onAnswerSelected="answerSelected"
    @onNextQuestion="current_question++"/>
  </main>
</template>


<script>
import Answers from './components/Answers.vue';
import Resultat from './components/Resultat.vue';
import InfoQuiz from './components/InfoQuiz.vue';
import StartQuiz from './components/StartQuiz.vue';
import Quiz from './components/Quiz.vue';
import User from './components/User.vue';

// data
import data from "./assets/js/data/newData.json";

export default {
  components: {StartQuiz,InfoQuiz,Resultat,Answers,Quiz,User,data},
  data(){
    return{
      myJson: data,
      current_question : 0, //index
    }
  },
  methods: {
    answerSelected(index){

      if(this.myJson[this.current_question].selected != null){
        return false;
      }
      this.myJson[this.current_question].selected = index;
    }
  },
}

</script>


<style scoped>

</style>
