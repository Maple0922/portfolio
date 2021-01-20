<template>
  <div id="app">
    <Header />
    <Main />
    <Hamburger :isActive="isActiveMenu" />
    <HamburgerMenu :isActive="isActiveMenu" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import Hamburger from "./components/Hamburger.vue";
import HamburgerMenu from "./components/HamburgerMenu.vue";

export default {
  name: "App",
  data() {
    return {
      isActiveMenu: false,
    };
  },
  components: {
    Header,
    Main,
    Hamburger,
    HamburgerMenu,
  },
};
</script>

<style lang="scss">
@import "./assets/scss/variables";
@import "./assets/scss/mixins";
@import "./assets/scss/reset";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
