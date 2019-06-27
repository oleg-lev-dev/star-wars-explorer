<template>
  <div class="wrap">
    <SearchStarships/>
    <StarshipsTable
      :starships="this.$store.state.starships"
      :isLoading="this.$store.state.isLoading"
      :next="this.$store.state.next"
      :prev="this.$store.state.prev"
    />
  </div>
</template>

<script>
  import StarshipsTable from '@/components/StarshipsTable.vue';
  import SearchStarships from '@/components/SearchStarships.vue';

  export default {
    name: 'home',
    components: {
      StarshipsTable,
      SearchStarships
    },

    mounted() {
      this.$store.dispatch('searchStarships', this.$route.query.search);
    }
  };
</script>

<style scoped lang="scss">
  .wrap {
    height: calc(100% - 80px);
  }
</style>
