<template>
  <div class="today_only">
    <h1>ONLY TODAY TODOS</h1>
    <div class="wrapper">
      <div class="item" v-for="item of today" :key="item.key">
        <div class="block">
            <div class="checkbox" @click="Complete_Todo(item)" :class="{ active: item.completed }"></div>
            <h3>{{ item.title }}</h3>
          </div>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis,
          facilis!
        </p>
        <span>{{ item.time }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
export default {
  name: "Today",
  computed: {
    ...mapGetters(["today"], mapActions),
  },
  methods:{
    Complete_Todo: function (check) {
      let sort = this.today.filter((item) => item.id == check.id)[0];
      sort.completed = !sort.completed;
    },
  }
};
</script>

<style>
</style>