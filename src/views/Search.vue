<template>
  <div class="search">
    <h1>This is an search page</h1>
    <div>{{ search }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: this.$route.params.word,

      searchResult: [],
    };
  },

  created(){
    
  }

  // methods: {

  // }
};
</script>
