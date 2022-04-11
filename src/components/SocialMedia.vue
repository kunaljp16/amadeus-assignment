<script>
import TwitterWhite from "../assets/icons/TwitterWhite.vue";
import YoutubeWhite from "../assets/icons/YoutubeWhite.vue";
export default {
  components: { TwitterWhite, YoutubeWhite },
};
</script>

<template>
  <div
    class="col-lg-3 col-md-6 col-sm-12 text-md-end text-sm-center"
  >
    <span class="pe-3"> Follow us on </span>
    <span class="pe-3">
      <a href="javascript:void(0)" aria-label="Twitter"><TwitterWhite /></a>
    </span>
    <span>
      <a href="javascript:void(0)" aria-label="YouTube"><YoutubeWhite /></a>
    </span>
  </div>
</template>

<style lang="scss">
@import "./../assets/scss/variables";

html[dir="rtl"] {
  .text-md-end{
    text-align: left;
  }
}

</style>
