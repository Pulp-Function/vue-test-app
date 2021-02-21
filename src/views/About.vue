<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div id="map"></div>
    <autocomplete
      source="https://api.github.com/search/repositories?q="
      results-property="items"
      results-display="full_name"
    ></autocomplete>
    <multiselect v-model="value" :options="options" :multiple="true"></multiselect>
    <p>The value is {{ value }}</p>
    <line-chart :data="{ '2017-05-13': 2, '2017-05-14': 5 }"></line-chart>
    <pie-chart
      :data="[
        ['Blueberry', 44],
        ['Strawberry', 23],
      ]"
    ></pie-chart>
  </div>
</template>

<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>

<style>
#map {
  width: 100%;
  height: 300px;
}
</style>

<script>
/* global mapboxgl */

import Multiselect from "vue-multiselect";
import Vue from "vue";
import Chartkick from "vue-chartkick";
import Chart from "chart.js";
import Autocomplete from "vuejs-auto-complete";

Vue.use(Chartkick.use(Chart));

export default {
  components: { Multiselect, Autocomplete },
  data() {
    return {
      value: null,
      options: ["list", "of", "options"],
    };
  },
  mounted: function() {
    this.setupMap();
  },
  methods: {
    setupMap: function() {
      mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_API_KEY;
      var map = new mapboxgl.Map({
        container: "map", // container id
        style: "mapbox://styles/mapbox/streets-v11", // style URL
        center: [-87.6298, 41.8781], // starting position [lng, lat]
        zoom: 9, // starting zoom
      });

      var marker = new mapboxgl.Marker().setLngLat([-87.6298, 41.8781]).addTo(map);

      console.log(marker);

      console.log(map);
    },
  },
};
</script>
