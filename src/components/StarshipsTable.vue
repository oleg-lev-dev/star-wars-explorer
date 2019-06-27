<template>
  <div class="wrapper">
    <Spinner :show="this.isLoading"/>
    <div class="table-wrap">

      <table v-if="!this.isLoading && starships.length"
             class="table uk-table uk-table-hover uk-table-divider uk-table-striped ">
        <thead>
        <tr class="">
          <th class="vk-table-column">Name</th>
          <th class="vk-table-column">Manufacturer</th>
          <th class="vk-table-column">Model</th>
        </tr>
        </thead>
        <tbody>

        <tr v-for="{name, manufacturer, model, id} in starships"
            v-on:click="onClick(id)">
          <td>{{name}}</td>
          <td>{{manufacturer}}</td>
          <td>{{model}}</td>
        </tr>
        </tbody>
      </table>

      <div v-if="noData" class="no-data">
        No Data
      </div>

    </div>
    <Pagination v-if="!noData"
                :nextLink="this.next"
                :prevLink="this.prev"/>
  </div>
</template>

<script>
  import Pagination from '@/components/Pagination.vue';
  import Spinner from '@/components/Spinner.vue';

  export default {
    name: 'starships-table',
    props: {
      starships: Array,
      next: String,
      prev: String,
      isLoading: Boolean,
    },
    components: {
      Pagination,
      Spinner
    },
    computed: {
      noData: function () {
        return !this.isLoading && !this.starships.length;
      }
    },
    methods: {
      onFetchNextPage() {
        this.$store.dispatch('fetchStarships', this.nextLink);
      },
      onFetchPrevPage() {
        this.$store.dispatch('fetchStarships', this.prevLink);
      },
      onClick(id) {
        this.$router.push({name: 'starship', params: {id}})
      }
    }
  };
</script>


<style scoped lang="scss">
  .wrapper {
    height: calc(100% - 80px);
    display: flex;
    flex-direction: column;
  }

  .table-wrap {
    flex: 1;
  }

  .table {
    td {
      cursor: pointer;
      text-align: left;
    }
  }

  .no-data {
    padding: 30px;
  }
</style>
