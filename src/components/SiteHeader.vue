<template>
  <div>
    <h1>{{title}}</h1>
    <router-link to="/my-trips">My Trips</router-link>
    <router-link to="/add-trip">Add Trip</router-link>
  </div>
</template>

<script>
export default {
  name: "SiteHeader",
  props: ["title"]
};
</script>
