<template>
  <Header />
  <Banner />
  <ContactUsLocation />
  <Footer />
  
</template>

<script>
import Header from "./components/Header.vue";
import Banner from "./components/Banner.vue";
import Footer from "./components/Footer.vue";
import ContactUsLocation from "./components/ContactUsLocation.vue";

export default {
  components: {
    Header,
    Banner,
    Footer,
    ContactUsLocation,
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
