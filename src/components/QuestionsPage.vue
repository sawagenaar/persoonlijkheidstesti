<template>
  <div class="questions-list">
    <div class="progress">
      <div class="bar" :style="{ width: `${currentQuestion / questions.length * 100}%` }"></div>
      <div class="status">
        {{ currentQuestion }} van de {{ questions.length }} vragen beantwoord
      </div>
    </div>
    <transition-group>
      <div class="box-question"
        v-for="(question, index) in questions"
        key="question.item"
        v-show="currentQuestion === index"
        >
        <div class="question"> {{ question.item }} </div>
        <div class="answers">
          <div class="answer"
            v-for="answer in question.answers"
            :key="answer.text"
            @click.prevent="chooseAnswer(answer.points)"
            >
              {{ answer.text }}
          </div>
        </div>
      </div>
    </transition-group>
  </div>

</template>

<script>
  export default {
    props: ["questions", "currentQuestion"],
    emits: ["question-answered"],
    methods: {
      chooseAnswer(points) {
        this.$emit('question-answered', points)
      }
    }
  }
</script>