<template>
  <GameIdeaGenerator />
  <Footer />
</template>

<script>
import GameIdeaGenerator from "./components/GameIdeaGenerator.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    GameIdeaGenerator,
    Footer,
  },
};
</script>

<style>
@keyframes background-animation {
  0% {
    background-color: #fcffa6;
  }
  25% {
    background-color: #c1ffd7;
  }
  50% {
    background-color: #b5deff;
  }
  75% {
    background-color: #cab8ff;
  }
  100% {
    background-color: #fcffa6;
  }
}

body {
  margin: 0;
  padding: 0;
  height: 100vh;

  animation-name: background-animation;
  animation-iteration-count: infinite;
  animation-duration: 20s;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
