<template>
  <div class="container">
    <div @click="chooseBooks('')">Hjem</div>
    <div @click="chooseBooks('fantasy')">Fantasy</div>
    <div @click="chooseBooks('kamasutra')">Kamasutra</div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  data() {
    return {};
  },
  methods: {
    chooseBooks(param) {
        //emit sender ut en funksjon som vi må høre etter i parent.
      this.$emit("choose-book-genre", param);
    },
  },
};
</script>

<style lang="css" scoped>
.container {
  background-color: grey;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 60%;
}
.container > div {
  margin-left: 10px;
}
</style>
