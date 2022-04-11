<script>
import Header from "./components/Header.vue";
import Banner from "./components/Banner.vue";
import MovieLibrary from "./components/MovieLibrary.vue";
import FavoriteCollectionsWrapper from "./components/FavoriteCollectionsWrapper.vue";
import ContactUsLocationWrapper from "./components/ContactUsLocationWrapper.vue";
import Footer from "./components/Footer.vue";

export default {
  components: {
    Header,
    Banner,
    MovieLibrary,
    FavoriteCollectionsWrapper,
    ContactUsLocationWrapper,
    Footer,
  },
};
</script>
<template>
  <Header />
  <Banner />
  <MovieLibrary />
  <!-- <FavoriteCollections /> -->
  <FavoriteCollectionsWrapper />
  <ContactUsLocationWrapper />
  <Footer />
</template>
<style lang="scss">
@import "./assets/scss/base.scss";

#app {
  width: 100%;
  font-weight: normal;
}
</style>
