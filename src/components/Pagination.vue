<template>
  <div class="pagination">
    <vk-button-group>
      <vk-button v-on:click="onFetchPrevPage"
                 :disabled="!this.prevLink">
        <vk-icons-arrow-left/>
        Prev
      </vk-button>
      <vk-button v-on:click="onFetchNextPage"
                 :disabled="!this.nextLink">
        Next
        <vk-icons-arrow-right/>
      </vk-button>
    </vk-button-group>
  </div>
</template>

<script>
  export default {
    name: 'pagination',
    props: {
      nextLink: String,
      prevLink: String,
    },
    methods: {
      onFetchNextPage() {
        this.$store.dispatch('fetchStarships', this.nextLink);
      },
      onFetchPrevPage() {
        this.$store.dispatch('fetchStarships', this.prevLink);
      }
    }
  };
</script>


<style scoped lang="scss">
  .pagination {
    padding: 20px;
    background-color: #f8f8f8;
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
