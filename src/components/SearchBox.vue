<template>
  <div class="position-relative container" style="z-index: 1">
    <div class="d-flex position-relative my-4" ref="search">
      <button
        @click="handleSearch"
        class="btn search-btn d-flex align-items-center h-100"
      >
        <img src="../assets/search.svg" alt="" />
      </button>
      <input
        v-model="searchField"
        @blur="onInputBlur"
        type="search"
        placeholder="search..."
        class="form-control bg-white w-100"
      />
    </div>
    <div v-if="showSug" class="suggestion bg-white w-100 text-left">
      <button @click="onCloseSug" class="close-sug btn btn-danger">
        close
      </button>
      <ul>
        <li v-if="!sugList.length" class="p-2 text-muted">No results</li>
        <li
          v-else
          v-for="{ title, id, slug } in sugList"
          :key="id"
          class="p-2 border-bottom"
        >
          <router-link :to="{ name: 'Single', params: { id } }">
            {{ title }}
          </router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchBox",
  data() {
    return {
      showSug: false,
      searchField: "",
      headerIsExtended: false,
      sugList: [],
    };
  },
  watch: {
    searchField(val) {
      if (val.length < 4) return;
      fetch(
        `https://api.giphy.com/v1/gifs/search?api_key=j8IJGL2jKygtWSHAmqE5Ji6JGe6BtgqU&q=${val}&limit=6`
      )
        .then((res) => res.json())
        .then((res) => {
          this.sugList = res.data;
          this.showSug = true;
        });
      console.log("this.sugList", this.sugList);
    },
  },
  methods: {
    handleSearch() {
      // this.$router.push({ name: "Search", params: { word: "asdf" } });
      this.$router.push({ name: "Search", params: { word: this.searchField } });
    },
    onCloseSug() {
      this.showSug = false;
      this.sugList = [];
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
.suggestion {
  /* height: 50px; */
  position: absolute;
  top: 100%;
  color: black;
}
.close-sug {
  position: absolute;
  right: 0;
  top: 0;
  font-size: 0.7em;
}
</style>
