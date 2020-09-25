<template>
  <div id="app">
    <img
      src="https://cdn.discordapp.com/attachments/392353546332405763/757956807778893954/cropped-animeworld-01.png"
      class="bd-placeholder-img bd-placeholder-img-lg featurette-image img-fluid mx-auto"
    />
    <Anime />
  </div>
</template>

<script>
import Anime from "./components/Anime.vue";

export default {
  name: "App",
  components: {
    Anime,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background-image: url("https://cdn.discordapp.com/attachments/392353546332405763/758277143858774016/704014176bc1f285c0c627b4910b64ae.jpg");
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 100vh;
}
</style>
