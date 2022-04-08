<script>
import useValidate from "@vuelidate/core";
import { required, email, minLength, sameAs } from "@vuelidate/validators";
import { reactive, computed } from "vue";
export default {
  components: {},
  setup() {
    const state = reactive({
      name: "",
      lastName: "",
      email: "",
      telephone: "",
      message: "",
      termsAndConditions: "",
    });

    const rules = computed(() => {
      return {
        name: { required, minLength: minLength(3) },
        lastName: { required, minLength: minLength(3) },
        email: { required, email },
        termsAndConditions: { required, sameAs: sameAs(() => true) },
      };
    });

    const v$ = useValidate(rules, state);

    return { v$, state };
  },

  methods: {
    contactUsForm: function () {
      this.v$.$validate();
      if (!this.v$.$error) {
        alert("form submitted successfully");
      } else {
        alert("error on page");
      }
      console.log("value = " + this.v$);
    },
  },
};
</script>

<template>
  <section class="container-fluid contactUsLocation">
    <div class="container">
      <div class="row mt-5">
        <div class="col-md-12 col-sm-12 col-lg-12">
          <h2>How to reach us</h2>
          <p>Lorem ipsum dolor sit amet, consetetur.</p>
        </div>
      </div>
      <div class="row mt-4 mb-5">
        <div class="col-lg-5 col-md-12 col-sm-12">
          <form @submit.prevent="submit" novalidate>
            <div class="row">
              <div class="col-md-6">
                <label for="name" class="form-label">Name<sup>*</sup></label>
                <input
                  type="text"
                  class="form-control"
                  :class="v$.name.$error ? ' border-danger' : ''"
                  id="name"
                  aria-describedby="name"
                  v-model="state.name"
                />
                <span class="error" v-if="v$.name.$error">{{
                  v$.name.$errors[0].$message
                }}</span>
              </div>
              <div class="col-md-6 mt-sm-4 mt-md-0 mt-xs-4">
                <label for="lastName" class="form-label"
                  >Last Name<sup>*</sup></label
                >
                <input
                  type="text"
                  class="form-control"
                  :class="v$.lastName.$error ? 'border-danger' : ''"
                  id="lastName"
                  aria-describedby="Last Name"
                  v-model="state.lastName"
                />
                <span class="error" v-if="v$.lastName.$error">{{
                  v$.lastName.$errors[0].$message
                }}</span>
              </div>
            </div>
            <div class="row mt-4">
              <div class="col-md-12">
                <label for="email" class="form-label">Email<sup>*</sup></label>
                <input
                  type="email"
                  class="form-control"
                  :class="v$.email.$error ? 'border-danger' : ''"
                  id="email"
                  aria-describedby="Email"
                  v-model="state.email"
                />
                <span class="error" v-if="v$.email.$error">{{
                  v$.email.$errors[0].$message
                }}</span>
              </div>
            </div>
            <div class="row mt-4">
              <div class="col-md-12">
                <label for="telephone" class="form-label">Telephone</label>
                <input
                  type="telephone"
                  class="form-control"
                  id="telephone"
                  aria-describedby="telephone"
                  v-model="state.telephone"
                />
              </div>
            </div>
            <div class="row mt-4">
              <div class="col-md-12">
                <label for="message" class="form-label">Message</label>
                <textarea
                  class="form-control"
                  id="message"
                  v-model="state.message"
                ></textarea>
              </div>
            </div>
            <div class="row mt-3">
              <div class="col-md-12 terms">
                <span class="d-block"><sup>*</sup> required fields</span>
                <div>
                  <span class="d-block mt-3">
                    <input
                      class="me-3 form-check-input"
                      type="checkbox"
                      value=""
                      id="termsAndConditions"
                    />
                    <label for="termsAndConditions">
                      I agree to the
                      <a href="javascript:void(0)">
                        <u>Terms &amp; Conditions</u>
                      </a>
                    </label>
                  </span>
                  <span class="error" v-if="v$.termsAndConditions.$error">
                    {{ v$.termsAndConditions.$errors[0].$message }}
                  </span>
                </div>
                <span class="d-block text-end mt-4">
                  <button @click="contactUsForm" type="submit" class="btn">
                    SUBMIT
                  </button>
                </span>
              </div>
            </div>
          </form>
        </div>
        <div
          class="col-lg-7 col-md-12 col-sm-12 mt-sm-5 mt-md-5 mt-lg-0 mt-xs-4"
        >
          <div class="mapOuter">
            <div class="gmapCanvas">
              <iframe
                id="gmapCanvas"
                src="https://maps.google.com/maps?q=Amadeus%20IT%20Group,%20C.%20Salvador%20de%20Madariaga,%201,%2028027%20Madrid&t=&z=13&ie=UTF8&iwloc=&output=embed"
                frameborder="0"
                scrolling="no"
                marginheight="0"
                marginwidth="0"
              ></iframe
              ><a href="https://123movies-to.org"></a>
              <a href="https://www.embedgooglemap.net"></a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.contactUsLocation {
  p,
  label,
  .terms {
    color: $light-gray2;

    u {
      color: $white;
    }
  }

  .inputStyle {
    background-color: $light-gray3;
    color: $white;
    border: 1px solid $light-gray3;
  }

  input,
  input[type="email"],
  textarea {
    @extend .inputStyle;
    &:focus {
      @extend .inputStyle;
    }
  }
  .form-check-input:checked {
    background-color: $black;
  }
  button:not(:disabled) {
    background-color: $yellow;
    width: 200px;
    color: #fff;
  }
  .mapOuter {
    position: relative;
    text-align: right;
    height: auto;
    width: auto;
  }
  #gmapCanvas {
    overflow: hidden;
    background: none !important;
    height: 464px;
    width: 100%;
  }
  .error {
    font-size: 12px;
    color: $red;
  }
}

@media (min-width: 375px) and (max-width: 767px) {
  .mt-xs-4 {
    margin-top: 1.5rem;
  }
}
@media (min-width: 768px) and (max-width: 1024px) {
}
</style>
