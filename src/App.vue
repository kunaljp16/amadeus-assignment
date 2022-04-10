<template>
  <Header />
  <Banner />
  <MovieLibrary />
  <FavoriteCollections />
  <ContactUsLocationWrapper />
  <Footer />
</template>

<script>
import Header from "./components/Header.vue";
import Banner from "./components/Banner.vue";
import MovieLibrary from "./components/MovieLibrary.vue";
import FavoriteCollections from "./components/FavoriteCollections.vue";
import ContactUsLocationWrapper from "./components/ContactUsLocationWrapper.vue";
import Footer from "./components/Footer.vue";

export default {
  components: {
    Header,
    Banner,
    MovieLibrary,
    FavoriteCollections,
    ContactUsLocationWrapper,
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
</style>
