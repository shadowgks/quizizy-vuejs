<template>
  <main>
    <!-- Background image -->
    <div class="bg_image"></div>
    <Quiz
      :questions="myJson[current_question]"
      :currentIndex="current_question"
      :lenght_data="myJson.length"
      @onAnswerSelected="answerSelected"
      @onNextQuestion="current_question++"
      v-if="current_question <= myJson.length - 1"
    />
    <Resultat v-else 
    :lenght_data="myJson.length" 
    :score="score"/>
  </main>
</template>


<script>
import Answers from "./components/Answers.vue";
import Resultat from "./components/Resultat.vue";
import InfoQuiz from "./components/InfoQuiz.vue";
import StartQuiz from "./components/StartQuiz.vue";
import Quiz from "./components/Quiz.vue";
import User from "./components/User.vue";

// data
import data from "./assets/js/data/newData.json";

export default {
  components: { StartQuiz, InfoQuiz, Resultat, Answers, Quiz, User, data },
  data() {
    return {
      myJson: data,
      current_question: 0, //index
      score: 0,
    };
  },
  methods: {
    answerSelected(index) {
      //disable selected
      if (this.myJson[this.current_question].selected != null) {
        return false;
      }
      //set selected some value
      this.myJson[this.current_question].selected = index;

      //increment Score
      if (this.myJson[this.current_question].isCorrect == index) {
        this.score++;
      }
    },
  },
};
</script>


<style scoped>
</style>
