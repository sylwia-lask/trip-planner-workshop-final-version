<template>
  <b-card
    :title="trip.country"
    :img-src="trip.photoLink"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2"
  >
    <b-form-checkbox
      :id="trip.id.toString()"
      v-model="checked"
      :name="trip.id.toString()"
      @change="$emit('selection-changed', trip.id)"
    >
     Check
    </b-form-checkbox>

    <b-card-text>
      <ul>
        <li v-for="thing in trip.thingsToSee" :key="thing">{{ thing }}</li>
      </ul>
      Rating:
      <b-icon
        icon="patch-minus"
        class="rating-icon"
        @click="decrementRating"
      ></b-icon
      >{{ rating
      }}<b-icon
        icon="patch-plus"
        class="rating-icon"
        @click="incrementRating"
      ></b-icon>
    </b-card-text>
  </b-card>
</template>

<script>
export default {
  name: "SingleTrip",
  props: ["trip"],
  data: function() {
    return {
      rating: this.trip.rating,
      checked: false
    };
  },
  methods: {
    incrementRating() {
      this.rating++;
    },
    decrementRating() {
      if (this.rating) {
        this.rating--;
      }
    },
  },
};
</script>

<style scoped>
.rating-icon {
  margin: 0 5px;
  cursor: pointer;
}

.rating-icon:hover {
  color: blue;
}
</style>
