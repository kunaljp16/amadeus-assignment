<template>
  <div class="col-lg-7 col-md-12 col-sm-12 mt-sm-5 mt-md-5 mt-lg-0 mt-xs-4">
    <div class="mapOuter">
      <div class="gMapCanvas">
        <iframe
          id="gMapCanvas"
          src="https://maps.google.com/maps?q=Amadeus%20IT%20Group,%20C.%20Salvador%20de%20Madariaga,%201,%2028027%20Madrid&t=&z=13&ie=UTF8&iwloc=&output=embed"
          frameborder="0"
          scrolling="no"
          marginheight="0"
          marginwidth="0"
        ></iframe>
        <a href="https://123movies-to.org"></a>
        <a href="https://www.embedgooglemap.net"></a>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.mapOuter {
  position: relative;
  text-align: right;
  height: auto;
  width: auto;
}
#gMapCanvas {
  overflow: hidden;
  background: none !important;
  height: 486px;
  width: 100%;
}
</style>
