<template>
  <div class="wrap">
    <h1>{{starship.name}}</h1>

    <vk-table :data="starshipTableData"
              narrowed>
      <vk-table-column title="Key" cell="key"></vk-table-column>
      <vk-table-column title="Val" cell="val"></vk-table-column>
    </vk-table>
  </div>
</template>

<script>

  export default {
    name: 'starship',

    computed: {
      starship: function () {
        const starship = this.$store.state.starships.find((starship = {}) => {
          return starship.id === this.$route.params.id;
        });

        return starship || {};
      },

      starshipTableData: function () {
        console.log('starship', this.starship);

        return  Object.keys(this.starship).reduce((acc, item) => ([...acc, {
          key: item,
          val: this.starship[item]
        }]), [])
      }
    },

    data: function () {
      return {}
    },

    mounted() {
      this.$store.dispatch('fetchStarship', this.$route.params.id);
    },
    methods: {
      onClick() {
        this.$router.push('about');
      }
    }
  };
</script>

<style scoped lang="scss">
  .wrap{
    padding: 20px 0 0;
    table{
      text-align: left;
    }
  }
</style>
