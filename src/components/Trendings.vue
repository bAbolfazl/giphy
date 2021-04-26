<template>
  <div class="container">
    <div
      v-for="{ id, images } in trendingData"
      :key="id"
      class="container__item"
    >
      <img :src="images.original.url" :alt="id" class="container__item__img" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Trendings",
  created() {
    // console.log("process.env", process.env);
    fetch(
      "https://api.giphy.com/v1/gifs/trending?api_key=j8IJGL2jKygtWSHAmqE5Ji6JGe6BtgqU&limit=6"
    )
      .then((res) => res.json())
      .then((res) => (this.trendingData = res.data));
  },

  data() {
    return {
      trendingData: Array,
    };
  },
};
</script>

<style scoped>
.container {
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;
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
</style>
