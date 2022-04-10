<script>
import Location from "./Location.vue";
import ContactUs from "./ContactUs.vue";
export default {
  components: { Location, ContactUs },
};
</script>

<template>
  <section class="container-fluid">
    <div class="container">
      <div class="row mt-5">
        <div class="col-md-12 col-sm-12 col-lg-12">
          <h2>How to reach us</h2>
          <p>Lorem ipsum dolor sit amet, consetetur.</p>
        </div>
      </div>
      <div class="row mt-4 mb-5">
        <ContactUs />
        <Location />
      </div>
    </div>
  </section>
</template>
