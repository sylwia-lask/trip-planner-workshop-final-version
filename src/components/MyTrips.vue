<template>
  <div class="ml-5">
    <h2>My trips</h2>
    <div v-if="selectedTrips.length">
      <h3>SelectedTrips</h3>
      <b-badge
        class="m-2"
        variant="primary"
        v-for="selectedTrip in selectedTrips"
        :key="selectedTrip.id"
        >{{ selectedTrip.country }}</b-badge
      >
    </div>
    <div v-else><h3>No trips selected</h3></div>

    <div class="row">
      <div v-for="trip in trips" :key="trip.id" class="col-sm-4">
        <single-trip
          :trip="trip"
          @selection-changed="addToSelectedTrips($event)"
        ></single-trip>
      </div>
    </div>
  </div>
</template>

<script>
import { myTrips } from "../data";
import SingleTrip from "./SingleTrip";

export default {
  name: "MyTrips",
  components: {
    SingleTrip,
  },
  data: function() {
    return {
      trips: [],
      selectedTrips: [],
    };
  },
  methods: {
    addToSelectedTrips(id) {
      if (this.selectedTrips.some((i) => i.id === id)) {
        this.selectedTrips = this.selectedTrips.filter((i) => i.id !== id);
      } else {
        this.selectedTrips.push(this.trips.find((i) => i.id === id));
      }
    },
  },
  mounted() {
    this.trips = myTrips;
  },
};
</script>
