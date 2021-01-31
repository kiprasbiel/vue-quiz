<template>
  <div>
    <b-nav>
      <b-nav-item disabled><b>Quizaroo</b></b-nav-item>
      <b-nav-item disabled>Counter {{ numCorrect }}/{{ totalAnswers }}</b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
name: "Header",
  props: [
      'numCorrect',
      'totalAnswers'
  ]
}
</script>

<style scoped>

</style>