<template>
  <div class="about">
    <h1>This is an about page</h1>
    <multiselect v-model="value" :options="options" :multiple="true"></multiselect>
    <p>The value is {{ value }}</p>
  </div>
</template>

<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>

<script>
import Multiselect from "vue-multiselect";

export default {
  components: { Multiselect },
  data() {
    return {
      value: null,
      options: ["list", "of", "options"],
    };
  },
};
</script>
