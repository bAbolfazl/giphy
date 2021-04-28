<template>
  <div v-for="{ id, images } in data" :key="id" class="container__item">
    <img :src="images.original.url" :alt="id" class="container__item__img" />
    <div class="overlay" @click="clickCard($event, id)">
      <div class="heart">
        <svg
          style="transition: .5s"
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
  </div>
</template>

<script>
export default {
  name: "xx",
  props: {
    data: String,
  },
  data() {
    return {
      fav: JSON.parse(localStorage.getItem("fav")) || [],
    };
  },
  created() {
    console.log("this.data", this.data);
    alert("created");
  },
  methods: {
    // handleClick: function(id) {},
    handleClick(id) {
      console.log("asdf", this.trendingData);
      if (this.fav.includes(id)) {
        const arr = this.fav.filter((item) => item !== id);
        this.fav = arr;
      } else {
        this.fav.push(id);
        //   localStorage.setItem("fav", JSON.stringify(id));
      }
      localStorage.setItem("fav", JSON.stringify(this.fav));
    },
    clickCard(event, id) {
      if (event.target.classList == "overlay")
        this.$router.push({ name: "Single", params: { id } });
    },
  },
};
</script>

<style scoped>
.container__item:hover .overlay {
  opacity: 1;
}

.container__item {
  width: 150px;
  height: 100px;
  margin: 5px;
  position: relative;
}
.container__item__img {
  object-fit: cover;
  width: 100%;
  height: 100%;
}
.overlay {
  background-color: rgba(0, 0, 0, 0.5);
  opacity: 0;
  position: absolute;
  right: 0;
  top: 0;
  width: 100%;
  height: 100%;
  display: flex;
  transition: 0.3s;
}
</style>
