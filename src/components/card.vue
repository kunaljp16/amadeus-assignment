<script>
export default {
  props: ["name", "image", "summary", "id"],
  emits: ["remove"],
  components: {},
  methods: {},
};
</script>

<template>
  <div class="col-md-4 col-md-4 col-sm-6 position-relative mb-4 showCard">
    <a href="javascript:void(0)" @click="$emit('remove')">
      <img src="./../assets/icons/CloseGrey.svg" alt="Delete Favorite" />
    </a>
    <img class="showImage" :src="image" :alt="name" />
    <div class="description">
      <h4 class="mt-2">{{ name }}</h4>
      <span class="summary" v-html="summary"></span>
    </div>
  </div>
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.showImage {
  object-fit: cover;
  width: -webkit-fill-available;
  height: 550px;
}

.showCard a {
  padding: 10px 14px;
  position: absolute;
  top: 10px;
  right: 23px;
  z-index: 5;
  background-color: $light-gray4;
  opacity: 0.7;
}

.description {
  background-color: $light-gray3;
  padding: 10px 15px;
  height: 126px;

  h4 {
    white-space: nowrap;
    width: 250px;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

.summary {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
}
</style>
