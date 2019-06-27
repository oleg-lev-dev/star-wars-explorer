<template>
  <div id="app">
    <vk-navbar>
      <vk-navbar-nav>
        <vk-navbar-logo>
          <router-link to="/">StarWars Explorer</router-link>
        </vk-navbar-logo>
      </vk-navbar-nav>
    </vk-navbar>
    <router-view/>
  </div>
</template>

<script>
  export default {
    name: 'app',
  };
</script>


<style lang="scss">
  html, body{
    height: 100%;
    min-height: 100%;
  }

  #app {
    height: 100%;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

</style>
