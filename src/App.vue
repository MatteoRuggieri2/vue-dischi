<template>
  <div id="app">

    <Header />
    <main>

      <MainContent />

    </main>

  </div>
</template>

<script>
import Header from "./components/Header.vue"
import MainContent from "./components/MainContent.vue"

export default {
  name: "App",
  components: {
      Header,
      MainContent
  },
};
</script>

<style lang="scss">
@import './style/general.scss';
@import './style/variables.scss';

  main {
    background-color: $secondary_color;
    min-height: calc( 100vh - 50px );
    padding: 50px 0;
  }

</style>
