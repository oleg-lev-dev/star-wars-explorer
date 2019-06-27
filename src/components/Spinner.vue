<template>
  <div v-if="this.show" class="spinner">
    <vk-spinner ratio="1.5"></vk-spinner>
  </div>
</template>

<script>

  export default {
    name: 'spinner',
    props: {
      show: Boolean,
    },
  };
</script>


<style scoped lang="scss">
  .spinner {
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
