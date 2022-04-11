<template>
  <section class="banner">
    <div
      id="carouselExampleCaptions"
      class="carousel slide"
      data-bs-ride="carousel"
    >
      <div class="carousel-indicators">
        <button
          type="button"
          data-bs-target="#carouselExampleCaptions"
          data-bs-slide-to="0"
          class="active"
          aria-current="true"
          aria-label="Slide 1"
        ></button>
        <button
          type="button"
          data-bs-target="#carouselExampleCaptions"
          data-bs-slide-to="1"
          aria-label="Slide 2"
        ></button>
      </div>
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img
            src="./../assets/images/batman.jpg"
            class="d-block w-100"
            alt="Batman banner"
          />
          <div class="carousel-caption d-none d-md-block">
            <h5>The Batman</h5>
            <p>
              When the Riddler, a sadistic serial killer, begins murdering key
              political figures in Gotham, Batman is forced to investigate the
              city's hidden corruption and question his family's involvement.
            </p>
          </div>
        </div>
        <div class="carousel-item">
          <img
            src="./../assets/images/spiderman.jpg"
            class="d-block w-100"
            alt="Spider man banner"
          />
          <div class="carousel-caption d-none d-md-block">
            <h5>Spiderman - No way Home</h5>
            <p>
              With Spider-Man's identity now revealed, Peter asks Doctor Strange
              for help. When a spell goes wrong, dangerous foes from other
              worlds start to appear, forcing Peter to discover what it truly
              means to be Spider-Man.
            </p>
          </div>
        </div>
      </div>
      <button
        class="carousel-control-prev"
        type="button"
        data-bs-target="#carouselExampleCaptions"
        data-bs-slide="prev"
      >
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button
        class="carousel-control-next"
        type="button"
        data-bs-target="#carouselExampleCaptions"
        data-bs-slide="next"
      >
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </section>
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.banner {
  background-image: url("./../assets/images/headerImage.jpg");
  background-size: cover;
  width: 100%;
  height: 500px;
  background-position: 10% 65%;

  .carousel-item {
    height: 500px;
  }
  .carousel-caption {
    background-color: $black-alpha50;
  }
}
@media (min-width: 375px) and (max-width: 767px) {
  .banner {
    height: 470px;
    background-position: 50% 66%;
    background-size: auto;
  }
}
</style>
