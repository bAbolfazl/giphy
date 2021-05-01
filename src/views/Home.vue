<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->

    <SearchBox />
    <Trendings />
  </div>
</template>

<script>
// @ is an alias to /src
import SearchBox from "@/components/SearchBox.vue";
import Trendings from "@/components/Trendings.vue";

export default {
  name: "Home",
  components: {
    SearchBox,
    Trendings,
  },
};
</script>

<style scoped>
/* .home {
  margin: 0 200px;
} */
</style>
