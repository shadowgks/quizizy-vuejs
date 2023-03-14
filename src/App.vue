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
    <Resultat
      v-else
      :lenght_data="myJson.length"
      :score="score"
      @onBtnShowAnswers="btnShowAnswers"
      v-if="!model_show_answers"
    />
    <Answers 
      v-if="model_show_answers" 
      :correctAnswers="correctAnswers"
    />
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
      myJson: data, //data json
      current_question: 0, //index
      score: 0,
      model_show_answers: false, //hide componente Show Resultat
      correctAnswers: [], //array answers selected user
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
        //set ansewrs correct in array
        this.correctAnswers.push(this.myJson[this.current_question]);
        console.log(this.correctAnswers);
      }
    },
    btnShowAnswers() {
      this.model_show_answers = true;
    },
  },
};
</script>


<style scoped>
</style>
