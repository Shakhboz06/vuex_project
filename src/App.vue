<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">HOMEPAGE</router-link>
      <router-link to="/today">ONLY TODAY</router-link>
    </div>
    <router-view />
  </div>
</template>
<script>
import { style } from "../Styles/CSS/style.css";
import Vue from "vue";
import * as VueAos from "vue-aos";
Vue.use(VueAos);
export default {
  mounted() {
    this.$store.dispatch("FILTER_TODO");
  },
};
</script>
<style>
</style>
