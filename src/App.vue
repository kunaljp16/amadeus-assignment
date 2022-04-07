<template>
  <Header />
  <Banner />
  <Footer />
</template>

<script>
import Header from "./components/Header.vue";
import Banner from "./components/Banner.vue";
import Footer from "./components/Footer.vue";

export default {
  components: {
    Header,
    Banner,
    Footer,
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
