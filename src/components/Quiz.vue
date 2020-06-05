<template>
  <div id="quiz">
    <div v-if="!end">
      <div v-for="(question, index) in questions" v-bind:key="index">
        <div v-if="index === questionIndex">
          <h2>{{ question.text }}</h2>
          <img v-bind:src="require('../assets/' + question.image + '.png')" />
        </div>
      </div>
      <div class="buttonContainer">
        <button class="button option" style="float: left" v-on:click="yes">
          Yes
        </button>
        <button class="button option" style="float: right" v-on:click="no">
          No
        </button>
      </div>
    </div>
    <div v-if="end">
      <div v-for="(ending, index) in endings" v-bind:key="index">
        <div v-if="index === questionIndex">
          <div v-if="!bastard">
            <h1>Not a bastard.</h1>
            <img v-bind:src="require('../assets/' + ending.image + '.png')" />
            <p>{{ ending.text }}</p>
          </div>
          <div v-else>
            <h1>Bastard.</h1>
            <img v-bind:src="require('../assets/' + ending.image + '.png')" />
            <p>{{ ending.text }}</p>
          </div>
        </div>
      </div>
      <div class="buttonContainer">
        <button style="float: left" class="button restart" v-on:click="restart">
          Restart
        </button>
        <a
          style="float: right"
          href="https://secure.actblue.com/donate/ms_blm_homepage_2019"
          target="_blank"
          class="button donate"
          >Donate</a
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Quiz",
  props: {},
  data: () => ({
    questions: [
      {
        text: "Are you a person?",
        image: "personwaving",
      },
      {
        text: "Do you have a job that pays you?",
        image: "money",
      },
      {
        text: "Do you typically wear blue or black?",
        image: "blue",
      },
      {
        text: "Do you have a gun?",
        image: "gun",
      },
      {
        text:
          "Do you love firing tear gas at peaceful protestors who fight for an end to police brutality against Black people?",
        image: "teargas",
      },
    ],
    endings: [
      {
        text:
          "You're a dog. You have no concept of human miseries such as war, capitalism, or Elon Musk. This is the best ending. You win.",
        image: "matapacos",
      },
      {
        text:
          "You're a volunteer. You provide a valuable service without even asking for pay. You're pretty great.",
        image: "volunteer",
      },
      {
        text:
          "You're a firefighter. You run into burning houses to save kittens. You're the definition of 'protect and serve'. Everyone loves you.",
        image: "firefighter",
      },
      {
        text:
          "You're a doctor, or a nurse. You work long hours, and your job is one of the most important ones humanity has. Definitely not a bastard.",
        image: "doctor",
      },
      {
        text:
          "You're a professional scuba diver. You probably shoot sharks with your spear gun and pet dolphins, or something.",
        image: "diver",
      },
      {
        text: "You're a bastard.",
        image: "bastard",
      },
    ],
    questionIndex: 0,
    bastard: false,
    end: false,
  }),
  methods: {
    // Go to next question
    yes: function() {
      this.questionIndex++;
      if (this.questionIndex == 5) {
        this.bastard = true;
        this.end = true;
      }
    },
    // Go to previous question
    no: function() {
      this.end = true;
    },
    restart: function() {
      this.end = false;
      this.questionIndex = 0;
      this.bastard = false;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.buttonContainer {
  width: 20em;
  display: inline-block;
  overflow: auto;
  white-space: nowrap;
  margin: 0px auto;
}

p {
  font-family: "Roboto", sans-serif;
  font-size: 21px;
}

.option {
  padding: 20px;
  width: 100px;
}

img {
  border: 2px solid #000;
}

.restart {
  padding: 20px;
  width: 150px;
}

.donate {
  padding: 20px;
  width: 100px;
}
</style>
