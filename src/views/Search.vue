<template>
  <div class="search container">
    <SearchBox />
    <SearchList />
  </div>
</template>

<script>
import SearchList from "../components/SearchList";
import SearchBox from "../components/SearchBox";

export default {
  name: "Search",
  components: { SearchList, SearchBox },

  // methods: {

  // }
};
</script>
