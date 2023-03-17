<template>
  <div>
    <form v-on:submit="searchAnime">
      <div class="form">
        <input type="text" v-model="animeName" name="anime" />
        <button class="button">Search</button>
      </div>
      <Spinner v-if="isLoading" size="massive" message="Loading..." />
      <Card v-bind:animeResponse="animeResponse" />
    </form>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./Card";
import Spinner from "vue-simple-spinner";

export default {
  name: "Input",
  components: {
    Card,
    Spinner,
  },
  data() {
    return {
      animeName: "",
      animeResponse: [],
      isLoading: false,
    };
  },
  methods: {
    searchAnime(event) {
      event.preventDefault();
      this.isLoading = true;
      axios
        .get("https://api.jikan.moe/v4/anime?q={this.animeName}&limit=10")
        .then((response) => {
          this.animeResponse = response.data.results;
          console.log("AnimeResponse: ", this.animeResponse);
        });
      this.isLoading = false;
      this.animeName = "";
    },
  },
};
</script>

<style>
.form {
  display: flex;
  width: 100%;
  height: 130px;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}

.button {
  display: inline-block;
  padding: 0.35em 1.2em;
  border: 0.1em solid black;
  margin: 0 0.3em 0.3em 0;
  border-radius: 0.3em;
  box-sizing: border-box;
  text-decoration: none;
  font-weight: 500;
  color: black;
  text-align: center;
  transition: all 0.3s;
}

.button:hover {
  color: white;
  background-color: black;
}

input {
  width: 250px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  background-color: white;
  background-position: 10px 10px;
  background-repeat: no-repeat;
  padding: 12px 20px;
  transition: width 0.6s ease-in-out;
}
</style>
