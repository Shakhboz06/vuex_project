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
export default {};
</script>
<style>
</style>
