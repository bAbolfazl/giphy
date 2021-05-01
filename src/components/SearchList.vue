<template>
  <div>
    <h3 class="mb-3">Results</h3>
    <div class="container">
      <CardsList :data="searchResult" />

      <!-- <div class="loading">loading...</div> -->
      <Loading v-if="is_loading" />
    </div>
  </div>
</template>

<script>
import CardsList from "../components/CardsList";
import Loading from "../components/Loading";

const limit = 20;
export default {
  name: "SearchList",
  components: { Loading, CardsList },
  data() {
    return {
      search: this.$route.params.word,
      searchResult: Array,
      offset: 0,
      is_loading: false,
    };
  },
  methods: {
    fetchSearched: function() {
      if (!this.search) return;
      // this.searchResult = "";
      // alert("hi");
      this.is_loading = true;
      console.log(this.searchResult);
      // debugger;

      fetch(
        `https://api.giphy.com/v1/gifs/search?api_key=j8IJGL2jKygtWSHAmqE5Ji6JGe6BtgqU&q=${this.search}&limit=${limit}&offset=${this.offset}`
      )
        .then((res) => res.json())
        .then((res) => {
          this.searchResult = res.data;
          console.log(res.data);
        })
        .catch((err) => console.log(err.mesage))
        .then(() => (this.is_loading = false));
    },
    // handleScroll: function() {
    //   const bodyHeight = document.body.scrollHeight;
    //   const bodyTop = document.body.scrollTop;
    //   const bodyOffset = document.body.offsetHeight;

    //   const bodyBottom = bodyHeight - bodyTop - bodyOffset;

    //   if (bodyBottom < 150) {
    //     ++this.offset;
    //     console.log(this.offset);
    //     // this.is_loading = true;
    //     // this.fetchSearched();
    //   }
    // },
  },
  watch: {
    $route() {
      this.fetchSearched();
    },
  },

  mounted() {
    //   window.addEventListener("scroll", this.handleScroll);

    this.fetchSearched();
  },
  //   unmounted() {
  //     window.removeEventListener("scroll", this.handleScroll);
  //   },
};
</script>

<style scoped>
.container {
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;
  /* margin: 0 200px; */
}

.container__item {
  width: 150px;
  height: 100px;
  margin: 5px;
}
.container__item__img {
  object-fit: cover;
  width: 100%;
  height: 100%;
}
.loading {
  display: flex;
  width: 100%;
  justify-content: center;
  margin: 20px 0;
  color: red;
}
</style>
