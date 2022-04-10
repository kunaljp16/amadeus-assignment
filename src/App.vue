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
import Footer from "./components/Footer.vue";
import ContactUsLocationWrapper from "./components/ContactUsLocationWrapper.vue";
import MovieLibrary from "./components/MovieLibrary.vue";
import FavoriteCollections from "./components/FavoriteCollections.vue";

export default {
  components: {
    Header,
    Banner,
    Footer,
    ContactUsLocationWrapper,
    MovieLibrary,
    FavoriteCollections,
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
