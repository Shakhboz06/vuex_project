<template>
  <div class="home">
    <h1>ALL TODOS</h1>
    <div class="today">
      <h2>FOR TODAY - {{ today.length }}</h2>
      <div class="wrapper">
        <div class="item" v-for="item of today" :key="item.key">
          <div class="block">
            <div
              class="checkbox"
              @click="Complete_Todo(item)"
              :class="{ active: item.completed }"
            ></div>
            <h3>{{ item.title }}</h3>
          </div>
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
          <span>{{ item.time }}</span>
        </div>
      </div>
    </div>
    <div class="tomorrow">
      <h2>TOMORROW - {{ tomorrow.length }}</h2>
      <div class="wrapper">
        <div class="item" v-for="item of tomorrow" :key="item.key">
          <div class="block">
            <div
              class="checkbox"
              @click="Complete_Todo(item)"
              :class="{ active: item.completed }"
            ></div>
            <h3>{{ item.title }}</h3>
          </div>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Saepe,
            sequi.
          </p>
          <span>{{ item.time }}</span>
        </div>
      </div>
    </div>
    <div class="later">
      <h2>LATER - {{ later.length }}</h2>
      <div class="wrapper">
        <div class="item" v-for="item of later" :key="item.key">
          <div class="block">
            <div
              class="checkbox"
              @click="Complete_Todo(item)"
              :class="{ active: item.completed }"
            ></div>
            <h3>{{ item.title }}</h3>
          </div>
          <p>
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ad,
            voluptas?
          </p>
          <span>{{ item.time }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { mapActions, mapGetters } from "vuex";
import HelloWorld from "@/components/HelloWorld.vue";
import Vue from "vue";
import * as VueAos from "vue-aos";
Vue.use(VueAos);

export default {
  name: "Home",
  computed: {
    ...mapGetters(["todos"], mapActions),
    ...mapGetters(["today"], mapActions),
    ...mapGetters(["tomorrow"], mapActions),
    ...mapGetters(["later"], mapActions),
  },
  methods: {
    // ...mapActions(["FILTER_TODO"]),
    Complete_Todo: function (check) {
      let sort = this.todos.filter((item) => item.id == check.id)[0];
      sort.completed = !sort.completed;
      
      localStorage.clear();
      localStorage.setItem("today", JSON.stringify(this.today));
      localStorage.setItem("tomorrow", JSON.stringify(this.tomorrow));
      localStorage.setItem("later", JSON.stringify(this.later));
    },
  },
  mounted() {
    localStorage.setItem("today", JSON.stringify(this.today));
    localStorage.setItem("tomorrow", JSON.stringify(this.tomorrow));
    localStorage.setItem("later", JSON.stringify(this.later));

    if (JSON.parse(localStorage.getItem("today"))) {
      this.today = JSON.parse(localStorage.getItem("today"));
    }
    if (JSON.parse(localStorage.getItem("tomorrow"))) {
      this.tomorrow = JSON.parse(localStorage.getItem("tomorrow"));
    }
    if (JSON.parse(localStorage.getItem("later"))) {
      this.later = JSON.parse(localStorage.getItem("later"));
    }
  },
  components: {
    HelloWorld,
  },
};
</script>

<style>
</style>