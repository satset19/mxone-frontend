<script>
import Footervue from "./components/Footer.vue";
import Hero from "./components/Hero.vue";
import Navbar from "./components/Navbar.vue";
import { mapActions } from "pinia";
import { useCounterStore } from "./stores/counter";
export default {
  name: "HomePage",
  components: {
    Navbar,
    Footervue,
    Hero,
  },
  methods: {
    ...mapActions(useCounterStore, ["fetchMovie", "fetchGenre"]),
  },
  created() {
    if (!localStorage.getItem("access_token")) {
      this.$router.push("/login");
    }
  },
};
</script>

<template>
  <Navbar />
  <RouterView />
  <!-- <Hero /> test -->
  <div class="parent">
    <Footervue />
  </div>
</template>

<style>
.parent {
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(5, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}
</style>
