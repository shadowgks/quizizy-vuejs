<template>
  <main>
    <!-- Background image -->
    <div class="bg_image"></div>
    <StartQuiz
      v-show="start_quiz"
      @onBtnShowInfoQuiz="onBtnShowInfoQuiz"
    />
    <InfoQuiz
      v-show="model_show_infoquiz"
      @onBtnShowUser="onBtnShowUser"
      @btn_quit="btn_quit"
    />
    <Quiz
      :questions="myJson[current_question]"
      :currentIndex="current_question"
      :lenght_data="myJson.length"
      @onAnswerSelected="answerSelected"
      @onNextQuestion="current_question++"
      v-if="current_question <= myJson.length - 1"
      v-show="model_show_quiz"
    />
    <Resultat
      v-else
      :lenght_data="myJson.length"
      :score="score"
      @onBtnShowAnswers="btnShowAnswers"
      v-if="!model_show_answers"
      @btn_quit="btn_quit"
    />
    <Answers 
      v-if="model_show_answers" 
      :arrCorrectAnswers="arrCorrectAnswers"
      @btn_quit="btn_quit"
    />
  </main>
</template>


<script>
import Answers from "./components/Answers.vue";
import Resultat from "./components/Resultat.vue";
import InfoQuiz from "./components/InfoQuiz.vue";
import StartQuiz from "./components/StartQuiz.vue";
import Quiz from "./components/Quiz.vue";

// data
import data from "./assets/js/data/newData.json";

export default {
  components: { StartQuiz, InfoQuiz, Resultat, Answers, Quiz, data },
  data() {
    return {
      myJson: data.sort(()=>Math.random() - 0.5), //data json
      current_question: 0, //index
      score: 0,
      arrCorrectAnswers: [], //array answers selected user

      //hide components
      start_quiz: true,
      model_show_infoquiz: false,
      model_show_quiz: false,
      model_show_answers: false,
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
        this.arrCorrectAnswers.push(this.myJson[this.current_question]);
      }
    },

    //btns show && hide
    btnShowAnswers() {
      this.model_show_answers = !this.model_show_answers;
    },
    onBtnShowInfoQuiz(){
      this.start_quiz = !this.start_quiz;
      this.model_show_infoquiz = !this.model_show_infoquiz;
    },
    onBtnShowUser(){
      this.model_show_infoquiz = !this.model_show_infoquiz;
      this.model_show_quiz = !this.model_show_quiz;
    },

    //btn reload page
    btn_quit(){
      location.reload();
    }
  },
};
</script>


<style scoped>
</style>
