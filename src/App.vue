<template>
  <div class="ctr">
    <questions
      v-if="questionsAnswered < questions.length"
      :questions="questions"
      :questionsAnswered="questionsAnswered"
      @questionAnswered="questionAnswered"
    />
    <result
      v-else
      :results="results"
      :correctAnswers="correctAnswers"
      :questions="questions"
    />
    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="questionsAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>

<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Questions,
    Result,
  },
  data() {
    return {
      questionsAnswered: 0,
      correctAnswers: 0,
      questions: [
        {
          q: "Which American State is called the 'Golden State'?",
          answers: [
            {
              text: "California",
              is_correct: true,
            },
            {
              text: "Idaho",
              is_correct: false,
            },
            {
              text: "Florida",
              is_correct: false,
            },
            {
              text: "Hawaii",
              is_correct: false,
            },
          ],
        },
        {
          q: "Which city was the first in the world to have a population of over one million?",
          answers: [
            {
              text: "London",
              is_correct: false,
            },
            {
              text: "Paris",
              is_correct: false,
            },
            {
              text: "Rome",
              is_correct: true,
            },
            {
              text: "Mexico City",
              is_correct: false,
            },
          ],
        },
        {
          q: "Pure gold is how many carats?",
          answers: [
            {
              text: "18",
              is_correct: false,
            },
            {
              text: "24",
              is_correct: true,
            },
            {
              text: "32",
              is_correct: false,
            },
          ],
        },
        {
          q: "What units is the intensity of sound measured in?",
          answers: [
            {
              text: "Ohms",
              is_correct: false,
            },
            {
              text: "Watts",
              is_correct: false,
            },
            {
              text: "Decibels",
              is_correct: true,
            },
            {
              text: "Kilograms",
              is_correct: false,
            },
          ],
        },
        {
          q: "In which month of the year is Thanksgiving, a holiday celebrated in the United States?",
          answers: [
            {
              text: "March",
              is_correct: false,
            },
            {
              text: "July",
              is_correct: false,
            },
            {
              text: "August",
              is_correct: false,
            },
            {
              text: "November",
              is_correct: true,
            },
          ],
        },
        {
          q: "Which musician narrated the children's TV series Thomas the Tank Engine?",
          answers: [
            {
              text: "Rick Astley",
              is_correct: false,
            },
            {
              text: "Rod Stewart",
              is_correct: false,
            },
            {
              text: "Paul Mccartney",
              is_correct: false,
            },
            {
              text: "Ringo Starr",
              is_correct: true,
            },
          ],
        },
        {
          q: "Goulash originally comes from which country?",
          answers: [
            {
              text: "Hungary",
              is_correct: true,
            },
            {
              text: "Romania",
              is_correct: false,
            },
            {
              text: "Bulgaria",
              is_correct: false,
            },
            {
              text: "Poland",
              is_correct: false,
            },
          ],
        },
        {
          q: "The River Thames is the second longest river in the UK, can you name the longest?",
          answers: [
            {
              text: "Trent",
              is_correct: false,
            },
            {
              text: "Tyne",
              is_correct: false,
            },
            {
              text: "Severn",
              is_correct: true,
            },
            {
              text: "Great Ouse",
              is_correct: false,
            },
          ],
        },
        {
          q: "In which language were Anne Frank's diaries originally written?",
          answers: [
            {
              text: "Russian",
              is_correct: false,
            },
            {
              text: "German",
              is_correct: false,
            },
            {
              text: "Dutch",
              is_correct: true,
            },
            {
              text: "French",
              is_correct: false,
            },
          ],
        },
        {
          q: "In traditional occupations what did a cooper make?",
          answers: [
            {
              text: "Barrels",
              is_correct: true,
            },
            {
              text: "Iron Plates",
              is_correct: false,
            },
            {
              text: "Belts",
              is_correct: false,
            },
            {
              text: "Shoes",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 3,
          max: 5,
          title: "Not a bad effort, but not great",
          desc: "Try again and see if you can beat your score",
        },
        {
          min: 6,
          max: 8,
          title: "You're very good!",
          desc: "You beat 75% of all players",
        },
        {
          min: 9,
          max: 10,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.correctAnswers++;
      }
      this.questionsAnswered++;
      console.log(this.correctAnswers);
    },
    reset() {
      this.questionsAnswered = 0;
      this.correctAnswers = 0;
    },
  },
};
</script>

<style>
</style>