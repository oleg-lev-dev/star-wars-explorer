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
      this.$store.dispatch('fetchStarships');
    }
  };
</script>

<style scoped lang="scss">
  .wrap{
    height: calc(100% - 80px);
  }
</style>
