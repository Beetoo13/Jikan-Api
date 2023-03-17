<template>
  <div>
    <ul class="cartas">
      <li class="fade-in" v-for="value in animeResponse" :key="value.title">
        <img v-bind:src="value.images.jpg.image_url" alt="image" />
        <h1>{{ value.title }}</h1>
        <h2>Number of episodes: {{ value.episodes }}</h2>
        <p>{{ value.synopsis }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["animeResponse"],
};
</script>

<style>
.cartas {
  display: flex;
  justify-content: space-evenly;
  align-items: stretch;
  flex-wrap: wrap;
  margin-top: 20px;
  margin-right: 5%;
  margin-left: 5%;
}

.cartas > li {
  align-items: center;
  width: 400px;
  height: 600px;
  border: 3px solid black;
  border-radius: 25px;
  text-align: center;
  list-style-type: none;
  margin-bottom: 20px;
}

li > h1 {
  padding-top: 10px;
  font-size: 1.6rem;
}

li > h2 {
  padding-top: 10px;
  font-size: 1.3rem;
}

li > p {
  padding-top: 10px;
  width: 90%;
  height: 120px;
  text-overflow: ellipsis;
  overflow: hidden;
  font-size: 0.8rem;
  margin-left: 5%;
  text-align: justify;
}

img {
  width: 100%;
  height: 60%;
  border-radius: 20px;
}

.fade-in {
  animation: fadeIn 1s;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
