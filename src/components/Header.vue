<template>
  <header>
    <SearchBox />
  </header>
</template>

<script>
import SearchBox from "../components/SearchBox.vue";
export default {
  name: "SearchBox",
  components: { SearchBox },
  data() {
    return {
      searchField: "",
    };
  },
};
</script>

<style scoped></style>
