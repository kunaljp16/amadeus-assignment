<template>
  <section class="copyRightWrapper grayBg">
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
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.copyRightWrapper {
  @media (min-width: 375px) and (max-width: 576px) {
    text-align: center;
  }

  .copyRight {
    p {
      font-size: 12px;
      color: $light-gray2;
    }
  }
}
</style>
