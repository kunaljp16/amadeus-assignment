<template>
  <section class="banner"></section>
</template>

<style lang="scss">
.banner {
  background-image: url("./../assets/images/headerImage.jpg");
  background-size: cover;
  width: 100%;
  height: 500px;
  background-position: 10% 65%;
}
@media (min-width: 375px) and (max-width: 767px) {
  .banner {
    height: 470px;
    background-position: 50% 66%;
    background-size: auto;
  }
}
@media (min-width: 768px) and (max-width: 1024px) {
}
</style>
