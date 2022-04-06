<template>
  <Header />
  <Banner />
</template>

<script>
import Header from "./components/Header.vue";
import Banner from "./components/Banner.vue";
export default {
  components: {
    Header,
    Banner
  },
};
</script>

<style lang="scss">
@import "./assets/scss/base.scss";

#app {
  width: 100%;
  font-weight: normal;
}

@media (min-width: 1024px) {
}
</style>
