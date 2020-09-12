<template>
  <div id="app">
    <site-header :title="formattedTitle"></site-header>
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
}
</style>
