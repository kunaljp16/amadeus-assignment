<script>
import Address from "./Address.vue";
import Copyright from "./Copyright.vue";
import SocialMedia from "./SocialMedia.vue";

export default {
  components: {Address, Copyright, SocialMedia },
};
</script>

<template>
  <footer class="footerWrapper grayBg">
    <div class="footerOuterSec">
      <section
        class="footer container pt-4 pb-4 col-sm-6 text-sm-center"
        id="footer"
      >
        <div class="row">
          <Address />
          <SocialMedia />
        </div>
      </section>
    </div>
    <Copyright />
  </footer>
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.footerWrapper,
.copyRightWrapper {
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
