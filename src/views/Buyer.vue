<template>
  <div class="home">
    <Navigation></Navigation>
    <BookList :context="'buyer'"></BookList>
    <button class="btn btn-space" @click="recommend()">RECOMMENDATIONS</button>
    <br style="padding-top: 100px" />
    <button class="btn btn-space" @click="change_data()">CHANGE DATA</button>
    <header>
      <!-- The header content -->
    </header>
  </div>
</template>

<style>
.btn {
  background-color: burlywood;
}

.btn-space {
  margin: 0 auto; /* Added */
  float: none; /* Added */
  margin-bottom: 50px; /* Added */
  width: 40%;
}
</style>

<script>
// @ is an alias to /src

import Navigation from "../components/Navigation.vue";
import BookList from "../components/BookList.vue";

export default {
  name: "Buyer",
  components: {
    Navigation,
    BookList,
  },
  data() {
    return {
      user: {},
    };
  },
  methods: {
    recommend() {
      this.$router.push("recommendations");
    },
    change_data() {
      localStorage.setItem("user", JSON.stringify(this.user));
      this.$router.push("change_data");
    },
  },
  mounted() {
    this.user = JSON.parse(localStorage.getItem("user"));
  },
};
</script>