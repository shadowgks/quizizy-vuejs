<template>
  <main>
    <!-- Background image -->
    <div class="bg_image"></div>

    <StartQuiz v-show="start_quiz" @onBtnShowInfoQuiz="onBtnShowInfoQuiz" />
    <InfoQuiz
      v-if="model_show_infoquiz"
      @onBtnShowQuiz="onBtnShowQuiz"
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
      myJson: data.sort(() => Math.random() - 0.5), //data json randome
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
    onBtnShowInfoQuiz() {
      this.start_quiz = !this.start_quiz;
      this.model_show_infoquiz = !this.model_show_infoquiz;
    },
    onBtnShowQuiz() {
      this.model_show_infoquiz = !this.model_show_infoquiz;
      this.model_show_quiz = !this.model_show_quiz;
    },
    btnShowAnswers() {
      this.model_show_answers = !this.model_show_answers;
    },

    //btn reload page
    btn_quit() {
      location.reload();
    },
  },
};
</script>


<style>
.half-arc {
    position: relative;
    width: 200px;
    height: 100px;
    border-top-left-radius: 120px;
    border-top-right-radius: 120px;
    border-bottom: 0;
    background: #d9d9d9;
    box-sizing: border-box;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
}

.half-arc:before {
    content: "";
    position: absolute;
    display: block;
    top: 0;
    left: 0;
    width: 100%;
    height: 200%;
    border-radius: 50%;
    background-image: conic-gradient(#9c27b0, #3f51b5 calc(var(--percentage, 0) / 2), #bbb 0);
    transition: transform .5s ease-in-out;
    z-index: 1;
    transform: rotate(270deg);
}

.half-arc:after {
    content: "";
    position: absolute;
    display: block;
    background: #dddddd;
    z-index: 2;
    width: calc(100% - 32px);
    height: calc(200% - 32px);
    border-radius: 50%;
    top: 16px;
    left: 16px;
}

.half-arc span {
    color: #673ab7;
    z-index: 3;
    text-align: center;
}
</style>
