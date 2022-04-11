<script>
import useValidate from "@vuelidate/core";
import { required, email, minLength } from "@vuelidate/validators";
import { reactive, computed } from "vue";
export default {
  components: {  },
  setup() {
    const state = reactive({
      name: "",
      lastName: "",
      email: "",
      telephone: "",
      message: "",
    });

    const rules = computed(() => {
      return {
        name: { required, minLength: minLength(3) },
        lastName: { required, minLength: minLength(3) },
        email: { required, email },
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
    },
  },
};
</script>

<template>
  <div class="col-lg-5 col-md-12 col-sm-12 contactUs">
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
            aria-required='true'
          />
          <span class="error" v-if="v$.name.$error">{{
            v$.name.$errors[0].$message
          }}</span>
        </div>
        <div class="col-md-6 mt-sm-4 mt-md-0 mt-xs-4">
          <label for="lastName" class="form-label">Last Name<sup>*</sup></label>
          <input
            type="text"
            class="form-control"
            :class="v$.lastName.$error ? 'border-danger' : ''"
            id="lastName"
            v-model="state.lastName"
            aria-required='true'
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
            v-model="state.email"
            aria-required='true'
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
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.contactUs {
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
    color: $white;
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
</style>
