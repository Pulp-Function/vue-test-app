<template>
  <div class="about">
    <h1>This is an about page</h1>
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

<script>
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
};
</script>
