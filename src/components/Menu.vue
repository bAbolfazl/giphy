<template>
  <div class="container mt-4 font-weight-bold text-white">
    <nav>
      <ul>
        <li v-for="{ id, title, src } of menuList" :key="id">
          <router-link :to="src">{{ title }}</router-link>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuList: [
        {
          id: 1,
          title: "home",
          src: "/",
        },
        {
          id: 2,
          title: "search",
          src: "/search",
        },
      ],
    };
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: center;
}
ul li {
  margin: 0 15px;
}

a {
  color: white !important;
}
/* .router-link-active {
  color: bisque;
} */
</style>
