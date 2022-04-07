<script>
import TwitterWhite from "./../assets/icons/TwitterWhite.vue";
import YoutubeWhite from "./../assets/icons/YoutubeWhite.vue";
export default {
  components: { TwitterWhite, YoutubeWhite },
  data() {
    return {};
  },
  methods: {},
};
</script>

<template>
  <footer class="footerWrapper">
    <div class="footerOuterSec">
      <section
        class="footer container pt-4 pb-4 col-sm-6 text-sm-center"
        id="footer"
      >
        <div class="row">
          <div class="col-lg-3 col-md-6 col-sm-12 text-md-start text-sm-center">
            <h6>Amadeus IT Group</h6>
            <address>
              <span class="d-block">C. Salvador de Madariaga, 1 </span>
              <span class="d-block">28027 Madrid</span>
              <span class="d-block"> Spain</span>
            </address>
          </div>
          <div
            class="col-lg-3 col-md-6 offset-lg-6 col-sm-12 text-md-end text-sm-center"
          >
            <span class="pe-3"> Follow us on </span>
            <span class="pe-3"
              ><a href="javascript:void(0)"><TwitterWhite /></a
            ></span>
            <span
              ><a href="javascript:void(0)"><YoutubeWhite /></a
            ></span>
          </div>
        </div>
      </section>
    </div>
    <section class="copyRightWrapper">
      <div class="copyRightOuterSec">
        <div class="copyRight container pt-3 pb-3">
          <div class="row">
            <div class="col-md-6 col-sm-12 text-md-start text-sm-center">
              <p class="m-0">
                Copyright &copy; 2022 Amadeus Hotels. All rights reserved.
              </p>
            </div>
            <div class="col-md-6 col-sm-12 text-md-end text-sm-center">
              <p class="m-0">
                Photos by <u>Felix Mooneeram</u> &amp; <u>Serge Kutuzov</u> on
                <u>Unsplash</u>
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </footer>
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.footerWrapper,
.copyRightWrapper {
  width: 100%;
  background-color: $dark-gray2;

  @media (min-width: 375px) and (max-width: 576px) {
    text-align: center;
  }

  .footer,
  .copyRight {
    p {
      font-size: 12px;
      color: $light-gray2;
    }
  }
  .footerOuterSec {
    border-bottom: 1px solid $light-gray;
  }
}
</style>
