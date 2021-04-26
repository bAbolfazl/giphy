<template>
  <div>
    <label for="">
      <button @click="handleSearch()">search</button>
      <input type="search" placeholder="search..." v-model="searchField" />
    </label>
  </div>
</template>

<script>
export default {
  name: "SearchBox",
  data() {
    return {
      searchField: "",
    };
  },
  methods: {
    handleSearch: function() {
      this.$router.push("serchBox");
    },
  },
};
</script>

<style scoped></style>
