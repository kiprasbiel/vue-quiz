<template>
  <div id="app">
    <Header
        :numCorrect="numCorrect"
        :totalAnswers="totalAnswers"
    />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox
              v-if="questions.length"
              :currentQuestion="questions[index]"
              :next="next"
              :increment="increment"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header";
import QuestionBox from "./components/QuestionBox";

export default {
  name: 'App',
  components: {
    Header,
    QuestionBox
  },
  data() {
    return {
      questions: [],
      index: 0,
      numCorrect: 0,
      totalAnswers: 0
    }
  },
  methods: {
    next(){
      this.index++
    },
    increment(isCorrect){
      if (isCorrect){
        this.numCorrect++
      }
      this.totalAnswers++
    }
  },
  mounted: function() {
    fetch('https://opentdb.com/api.php?amount=10&category=27&difficulty=medium&type=multiple', {
      method: 'get'
    })
        .then((response) => {
          return response.json()
    }).then((jsonData) => {
      this.questions = jsonData.results
    })
  }
}
</script>

<style>
#app {
}
</style>
