<template>
  <div class="search-starships">
    <input class="uk-input uk-form-width-large uk-margin-small-right"
           type="text"
           placeholder="Search starship by name"
           v-model="searchText">
  </div>
</template>

<script>
  export default {
    name: 'search-starships',
    data: function () {
      return {
        searchText: ''
      };
    },
    watch: {
      searchText: function (value = '') {
        this.$store.dispatch('searchStarships', value.trim());
        this.$router.replace({name: "home", query: {search: value.trim()}})
      }
    },
    mounted() {
      this.searchText = this.$route.query.search;
    }
  };
</script>

<style scoped lang="scss">
  .search-starships {
    padding: 20px;
  }
</style>
