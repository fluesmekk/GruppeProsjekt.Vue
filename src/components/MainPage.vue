<template>
  <div class="grid-container">
    <div class="book" v-for="book in books" :key="book.id">
      <img :src="book.img" />
      <p class="title">
        <b>{{ book.name }}</b>
      </p>
      <p>{{ book.author }}</p>
      <p>{{ book.genre }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "MainPage",
  async created() {
    let response = await axios.get("http://localhost:3000/books");
    this.books = response.data;
  },
  props: { chosenbooks: String },
  data() {
    return {
      books: [],
    };
  },
  methods: {
    async chooseBooks() {
        console.log(this.chosenbooks);
        let response = await axios.get(`http://localhost:3000/books?q=${this.chosenbooks}`);
        return response.data;
    },
  },
  //watch ser på propertien chosenbooks og gjør det den har i funksjonen sin
  watch: {
    async chosenbooks() {
      this.books = await this.chooseBooks();
    },
  },
};
</script>

<style lang="css" scoped>
.grid-container {
  margin-top: 20px;
  display: grid;
  grid: 1fr 1fr / 1fr 1fr 1fr;
}
.book {
  display: flex;
  flex-direction: column;
  width: 60%;
  margin-left: 20px;
  height: auto;
  margin-bottom: 6px;
  background-color: grey;
  border: solid grey 1px;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  box-shadow: 0, 0, 0 rgba(0, 0, 0, 0.3);
  align-items: flex-start;
}

.book > p {
  /* line-height: 1px;  */
  margin-bottom: 2px;
}

img {
  /* height: 160px; */
  width: 100%;
  height: auto;
}

.title {
  color: black;
}
</style>
