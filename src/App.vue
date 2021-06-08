<template>
  <div>
    <!-- @ tilsvarer det vi emitter, og kjører det vi har inne i "" -->
    <NavBar @choose-book-genre="chooseBookGenre" />
    <!-- : tilsvarer en prop som vi hører på inne i child -->
    <MainPage :chosenbooks="chosenBookGenre" />
    <!-- Her bruker vi ikke en eventbus eller vuex så da sender vi videre fra navbar -> app.vue -> mainpage -->
  </div>
</template>

<script>
import MainPage from "./components/MainPage.vue";
import NavBar from "./components/NavBar.vue";

export default {
  name: "App",
  components: {
    MainPage,
    NavBar,
  },
  data() {
    return {
      chosenBookGenre: "",
    };
  },
  methods: {
    chooseBookGenre(param) {
      this.chosenBookGenre = param;
    },
  },
};
</script>

<style>
body,
html {
  height: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
