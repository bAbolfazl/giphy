<template>
  <div class="container">
    <Loading v-if="isLoading" />
    <template v-else>
      <CardsList :data="trendingData" />
      <div class="w-100 text-center my-4">
        <button @click="onClick" class="btn btn-info">Update</button>
      </div>
    </template>
    <!-- <div
      v-for="{ id, images } in trendingData"
      :key="id"
      class="container__item"
    >
      <img :src="images.original.url" :alt="id" class="container__item__img" />
      <div class="overlay">
        <div class="heart">
          <svg
            @click="handleClick(id, fav)"
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 24 24"
            :fill="fav.includes(id) ? '#f00' : '#fff'"
            stroke="#000000"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path
              d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"
            ></path>
          </svg>
        </div>
      </div>
    </div> -->
  </div>
</template>

<script>
import CardsList from "../components/CardsList";
import Loading from "../components/Loading";

export default {
  name: "Trendings",
  components: { CardsList, Loading },
  data() {
    return {
      isLoading: false,
      page: 1,
      trendingData: Array,
      fav: JSON.parse(localStorage.getItem("fav")) || [],
    };
  },
  methods: {
    onClick() {
      ++this.page;
      this.isLoading = true;
      fetch(
        `https://api.giphy.com/v1/gifs/trending?api_key=j8IJGL2jKygtWSHAmqE5Ji6JGe6BtgqU&limit=18&offset=${this
          .page * 18}`
      )
        .then((res) => res.json())
        // .then(console.log)
        .then((res) => {
          this.trendingData.push(...res.data);
          this.isLoading = false;
        });
    },
  },
  created() {
    // console.log("process.env", process.env);
    this.isLoading = true;

    fetch(
      `https://api.giphy.com/v1/gifs/trending?api_key=j8IJGL2jKygtWSHAmqE5Ji6JGe6BtgqU&limit=18`
    )
      .then((res) => res.json())
      .then((res) => {
        this.trendingData = res.data;
        this.isLoading = false;
      });
  },
};
</script>

<style scoped>
.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
}
</style>
