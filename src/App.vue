<template>
  <div id="app">
    <site-header :title="formattedTitle"></site-header>
    <button @click="changeTitle">Change title</button>
    <router-view></router-view>
  </div>
</template>

<script>
import SiteHeader from "./components/SiteHeader";

export default {
  name: "App",
  components: {
    SiteHeader,
  },
  data: function() {
    return {
      title: "Inny tytuł"
    };
  },
  computed: {
    formattedTitle() {
      return this.title + "***";
    }
  },
  methods: {
    changeTitle() {
      this.title = "Tytuł po zmianie";
    },
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
</style>
