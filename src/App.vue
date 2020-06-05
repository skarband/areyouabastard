<template>
  <div id="app">
    <div v-if="!quizStart">
      <h1 style="padding-left:0.5em; padding-right: 0.5em">
        Are you a bastard?
      </h1>
      <img src="@/assets/hat.png" />
      <button class="button" @click="quizStart = true">
        Take the quiz to find out
      </button>
    </div>
    <div v-if="quizStart">
      <Quiz />
    </div>
  </div>
</template>

<script>
import Quiz from "./components/Quiz.vue";
document.title = "Are you a bastard?"

export default {
  name: "App",
  components: {
    Quiz,
  },
  data: () => ({
    quizStart: false,
  }),
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Archivo+Black&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");

#app {
  font-family: "Archivo Black", "Roboto", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
}

body {
  background-color: #f3f3f3;
}

img {
  margin-top: -1em;
  margin-bottom: 1.5em;
  max-height: 20em;
  max-width: 100%;
  display: block;
  margin-left: auto;
  margin-right: auto;
}

h1 {
  letter-spacing: 1px;
  /* padding-bottom: 0.5em; */
  padding-top: 1em;
}

h2 {
  font-weight: 400;
  padding-bottom: 0.5em;
  padding-top: 1.5em;
}

.button {
  font-family: "Roboto", sans-serif;
  text-align: center;
  text-transform: uppercase;
  cursor: pointer;
  font-size: 20px;
  letter-spacing: 3px;
  position: relative;
  border: none;
  padding: 20px;
  width: 250px;
  text-align: center;
  transition-duration: 0.2s;
  line-height: 30px;
  border: 2px solid #000;
  background: #f3f3f3;
}

@media (hover: none) {
   .button {
      background: #f3f3f3;
      border: 2px solid #000;
      color: #000;
   }
}

.button:hover {
  background: #000;
  color: #f3f3f3;
  /* border: 4px solid #000; */
}

.button:focus {
  outline: 0;
}

a {
  color: #000;
  text-decoration: none;
}

div {
  width: 100%;
  max-width: 40em;
  margin-left: auto;
  margin-right: auto;
}
</style>
