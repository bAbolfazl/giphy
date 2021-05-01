<template>
  <div class="container row mx-auto">
    <div class="col-lg-3">
      <div>
        <img
          :src="currentGif?.user?.avatar_url"
          alt="profile"
          class="profile-img"
        />
        <div class="mt-3 text-muted">
          {{ currentGif?.username }}
        </div>
      </div>
    </div>
    <div class="col-lg-9">
      <h1 class="small">{{ currentGif?.title }}</h1>
      <img :src="currentGif?.images?.downsized_large?.url" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentGif: [],
    };
  },

  created() {
    fetch(
      `https://api.giphy.com/v1/gifs/${this.$route.params.id}?api_key=j8IJGL2jKygtWSHAmqE5Ji6JGe6BtgqU`
    )
      .then((res) => res.json())
      .then((res) => {
        this.currentGif = res.data;
      });
  },
};
</script>

<style scoped>
.profile-img {
  border-radius: 100%;
  width: 70px;
  height: 70px;
}
</style>
