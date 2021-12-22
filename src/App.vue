<template>
  <div id="app">

    <Header />
    <main>

    </main>

  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Header from "./components/Header.vue"

export default {
  name: "App",
  components: {
      Header,
  },
};
</script>

<style lang="scss">
@import './style/general.scss';

  main {
    background-color: #1e2d3b;
  }

</style>
