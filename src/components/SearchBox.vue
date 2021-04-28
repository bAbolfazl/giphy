<template>
  <div class="d-flex position-relative my-4" ref="search">
    <button
      @click="handleSearch"
      class="btn search-btn d-flex align-items-center h-100"
    >
      <img src="../assets/search.svg" alt="" />
    </button>
    <input
      v-model="searchField"
      type="search"
      placeholder="search..."
      class="form-control bg-white w-100"
    />
  </div>
</template>

<script>
export default {
  name: "SearchBox",
  data() {
    return {
      searchField: "",
      headerIsExtended: false,
    };
  },
  methods: {
    handleSearch() {
      // this.$router.push({ name: "Search", params: { word: "asdf" } });
      this.$router.push({ name: "Search", params: { word: this.searchField } });
    },
    // handleScroll: function() {
    //   //   const bodyHeight = document.body.scrollHeight;
    //   //   const bodyTop = document.body.scrollTop;
    //   //   const bodyOffset = document.body.offsetHeight;

    //   //   const bodyBottom = bodyHeight - bodyTop - bodyOffset;
    //   this.$ref.input.getBoundingClientRect().top;
    //   console.log(this.$ref.input);

    //   //   if (bodyBottom < 150) {
    //   //     ++this.offset;
    //   //     console.log(this.offset);
    //   //     // this.is_loading = true;
    //   //     // this.fetchSearched();
    //   //   }
    // },
  },
  //   created() {
  //     window.addEventListener("scroll", this.handleScroll);
  //   },
  //   unmounted() {
  //     window.removeEventListener("scroll", this.handleScroll);
  //   },
};
</script>

<style scoped>
.search-btn {
  background: rgba(0, 0, 0, 0)
    linear-gradient(45deg, rgb(153, 51, 255) 0%, rgb(255, 102, 102) 100%) repeat
    scroll 0% 0%;
}
.search-btn {
  position: absolute;
  right: 0;
  top: 0;
}
</style>
