<template>
  <div class="ml-5 mr-5">
    <h2>Add trip</h2>
    <form @submit.prevent="submitForm">
      <b-form-input
        v-model="country"
        placeholder="Enter country"
        class="mt-2"
        required
      ></b-form-input>
      <b-form-input
        v-model="cityOfResidence"
        placeholder="Enter city of residence"
        class="mt-2"
      ></b-form-input>
      <b-form-datepicker
        id="date"
        v-model="date"
        class="mt-2"
        :date-format-options="{
          year: 'numeric',
          month: 'numeric',
          day: 'numeric',
        }"
        required
      ></b-form-datepicker>
      <b-form-input
        v-model="photoLink"
        placeholder="Enter photo link"
        class="mt-2"
        required
      ></b-form-input>
      <b-form-input
        v-model="rating"
        type="number"
        min="0"
        placeholder="Enter rating"
        class="mt-2"
        required
      ></b-form-input>
      <b-form-input
        v-model="thingsToSeeInput"
        placeholder="Type things to see"
        class="mt-2"
      ></b-form-input>
      <b-button variant="success" @click="addThingToSee"
        >Save thing to see</b-button
      >
      <ul>
        <li v-for="(thing, index) in thingsToSee" :key="index">{{ thing }}</li>
      </ul>

      <b-button type="submit" variant="primary">Submit</b-button>
    </form>
  </div>
</template>

<script>
import {myTrips} from '../data';

export default {
  name: "AddTrip",
  data: function() {
    return {
      country: "",
      cityOfResidence: "",
      date: "",
      thingsToSee: [],
      photoLink: "",
      rating: 0,
      thingsToSeeInput: "",
    };
  },
  methods: {
    addThingToSee() {
      this.thingsToSee.push(this.thingsToSeeInput);
      this.thingsToSeeInput = "";
    },
    submitForm() {
      const trip = {
        id: myTrips.length + 1,
        country: this.country,
        cityOfResidence: this.cityOfResidence,
        date: this.date,
        thingsToSee: this.thingsToSee,
        photoLink: this.photoLink,
        rating: this.rating
      };

      myTrips.push(trip);
      this.$router.push('/my-trips');
    }
  },
};
</script>
