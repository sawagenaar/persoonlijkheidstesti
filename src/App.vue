<template>
  <div class="container">
    <questions-page
      v-if="currentQuestion < questions.length"
      :questions="questions"
      :currentQuestion="currentQuestion"
      @question-answered="questionAnswered"
    ></questions-page>
    <result-page
      v-else
      :results="results"
      :totalResult="totalResult"
    ></result-page>
    <button type="button" class="reset-btn" @click="resetQuiz">Reset</button>
  </div>
</template>

<script>
import { questions, results } from './_config';
import QuestionsPage from './components/QuestionsPage.vue';
import ResultPage from './components/ResultPage.vue';
export default {
  components: { QuestionsPage, ResultPage },
  data() {
    return {
      questions: questions,
      results: results,
      currentQuestion: 0,
      totalResult: 0,
    }
  },
  methods: {
    questionAnswered(points) {
      if (points) {
        this.totalResult += points;
      }
      this.currentQuestion++;
    },
    resetQuiz() {
      this.totalResult = 0;
      this.currentQuestion = 0;
    }
  }
}
</script>

