<template>
  <div id="app">
    <Title />
    <Input />
  </div>
</template>

<script>
import Title from "./components/Title";
import Input from "./components/Input";

export default {
  name: "App",
  components: {
    Title,
    Input,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: rgb(255, 241, 213);
}
#app {
  font-family: "Montserrat Medium", sans-serif;
}
</style>
