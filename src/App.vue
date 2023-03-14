<template>
  <main>
    <!-- Background image -->
    <div class="bg_image">
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
    </div>
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
.md-stepper-horizontal {
	display:table;
	width:100%;
	margin:0 auto;
	background-color:#FFFFFF;
	box-shadow: 0 3px 8px -6px rgba(0,0,0,.50);
}
.md-stepper-horizontal .md-step {
	display:table-cell;
	position:relative;
	padding:24px;
}
.md-stepper-horizontal .md-step:hover,
.md-stepper-horizontal .md-step:active {
	background-color:rgba(0,0,0,0.04);
}
.md-stepper-horizontal .md-step:active {
	border-radius: 15% / 75%;
}
.md-stepper-horizontal .md-step:first-child:active {
	border-top-left-radius: 0;
	border-bottom-left-radius: 0;
}
.md-stepper-horizontal .md-step:last-child:active {
	border-top-right-radius: 0;
	border-bottom-right-radius: 0;
}
.md-stepper-horizontal .md-step:hover .md-step-circle {
	background-color:#757575;
}
.md-stepper-horizontal .md-step:first-child .md-step-bar-left,
.md-stepper-horizontal .md-step:last-child .md-step-bar-right {
	display:none;
}
.md-stepper-horizontal .md-step .md-step-circle {
	width:30px;
	height:30px;
	margin:0 auto;
	background-color:#999999;
	border-radius: 50%;
	text-align: center;
	line-height:30px;
	font-size: 16px;
	font-weight: 600;
	color:#FFFFFF;
}
.md-stepper-horizontal.green .md-step.active .md-step-circle {
	background-color:#00AE4D;
}
.md-stepper-horizontal.orange .md-step.active .md-step-circle {
	background-color:#F96302;
}
.md-stepper-horizontal .md-step.active .md-step-circle {
	background-color: rgb(33,150,243);
}
.md-stepper-horizontal .md-step.done .md-step-circle:before {
	font-family:'FontAwesome';
	font-weight:100;
	content: "\f00c";
}
.md-stepper-horizontal .md-step.done .md-step-circle *,
.md-stepper-horizontal .md-step.editable .md-step-circle * {
	display:none;
}
.md-stepper-horizontal .md-step.editable .md-step-circle {
	-moz-transform: scaleX(-1);
	-o-transform: scaleX(-1);
	-webkit-transform: scaleX(-1);
	transform: scaleX(-1);
}
.md-stepper-horizontal .md-step.editable .md-step-circle:before {
	font-family:'FontAwesome';
	font-weight:100;
	content: "\f040";
}
.md-stepper-horizontal .md-step .md-step-title {
	margin-top:16px;
	font-size:16px;
	font-weight:600;
}
.md-stepper-horizontal .md-step .md-step-title,
.md-stepper-horizontal .md-step .md-step-optional {
	text-align: center;
	color:rgba(0,0,0,.26);
}
.md-stepper-horizontal .md-step.active .md-step-title {
	font-weight: 600;
	color:rgba(0,0,0,.87);
}
.md-stepper-horizontal .md-step.active.done .md-step-title,
.md-stepper-horizontal .md-step.active.editable .md-step-title {
	font-weight:600;
}
.md-stepper-horizontal .md-step .md-step-optional {
	font-size:12px;
}
.md-stepper-horizontal .md-step.active .md-step-optional {
	color:rgba(0,0,0,.54);
}
.md-stepper-horizontal .md-step .md-step-bar-left,
.md-stepper-horizontal .md-step .md-step-bar-right {
	position:absolute;
	top:36px;
	height:1px;
	border-top:1px solid #DDDDDD;
}
.md-stepper-horizontal .md-step .md-step-bar-right {
	right:0;
	left:50%;
	margin-left:20px;
}
.md-stepper-horizontal .md-step .md-step-bar-left {
	left:0;
	right:50%;
	margin-right:20px;
}
</style>
