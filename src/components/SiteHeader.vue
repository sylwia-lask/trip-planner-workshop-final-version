<template>
  <div>
    <b-navbar type="dark" variant="info">
      <b-navbar-brand href="#">Trip Planner</b-navbar-brand>
      <b-navbar-nav>
        <b-nav-item to="/my-trips">My Trips</b-nav-item>
        <b-nav-item to="/add-trip">Add Trip</b-nav-item>
      </b-navbar-nav>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "SiteHeader",
  props: ["title"],
};
</script>
