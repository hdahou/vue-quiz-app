<template>
  <div class="result">
    <div class="title">
      You got {{ correctAnswers }} out of {{ questions.length }} ...
      {{ results[resultIndex].title }}
    </div>
    <div class="desc">{{ results[resultIndex].desc }}</div>
  </div>
</template>

<script>
export default {
  props: ["results", "correctAnswers", "questions"],
  computed: {
    resultIndex() {
      let index = 0;
      this.results.forEach((e, i) => {
        if (e.min <= this.correctAnswers && e.max >= this.correctAnswers) {
          index = i;
        }
      });
      return index;
    },
  },
};
</script>

<style>
</style>