<template>
  <main>
    <!-- Background image -->
    <div class="bg_image"></div>
    <StartQuiz />
    <!-- <InfoQuiz /> -->
  </main>
</template>


<script>
import Answers from './components/Answers.vue';
import Resultat from './components/Resultat.vue';
import InfoQuiz from './components/InfoQuiz.vue';
import StartQuiz from './components/StartQuiz.vue';
import Quiz from './components/Quiz.vue';
import User from './components/User.vue';

export default {
  components: {StartQuiz,InfoQuiz,Resultat,Answers,Quiz,User},
  data(){

  },
  methods: {
    
  },
}

</script>


<style scoped>

</style>
