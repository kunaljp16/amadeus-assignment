<script>
export default {
  props: {
    getSearchName: Function,
    filterShows: Array,
    getIdFromList: Function,
  },
  data() {
    return {
      isInputHasValue: false,
    };
  },
  methods: {
    onNameSearch() {
      this.$emit("search", this.name);
    },
    checkInputTyping: function () {
      if (this.name !== "") {
        this.isInputHasValue = true;
      } else {
        this.isInputHasValue = false;
      }
    },
  },
};
</script>

<template>
  <form class="form-inline">
    <input
      class="form-control mr-sm-2 search"
      type="search"
      placeholder="Search"
      aria-label="Search"
      v-model="name"
      @keyup="checkInputTyping"
      autocomplete="off"
      @input="$emit('update:modelValue', $event.target.value)"
    />
    <div class="searchResult" v-if="isInputHasValue">
      <ul>
        <li
          v-for="show in filterShows"
          :key="show.id"
          @click="$emit('update:modelValue', getIdFromList(show.id))"
        >
          {{ show.name }}
        </li>
      </ul>
    </div>
  </form>
</template>

<style lang="scss">
@import "./../assets/scss/variables";

.search {
  background: url("./../assets/icons/SearchWhite.svg") no-repeat;
  background-color: $dark-gray2;
  color: $white;
  background-position: 7px 6px;
  padding-left: 36px;

  &:focus {
    background-color: $dark-gray2;
    color: $white;
  }
}

.searchResult {
  position: absolute;
  background: $dark-gray2;
  width: fit-content;
  z-index: 10;
  max-height: 200px;
  overflow-y: scroll;
  min-width: 296px;

  ul {
    padding: 0;
    margin: 0;
    li {
      list-style: none;
      padding: 8px;
      &:hover {
        color: $light-gray4;
        background-color: $light-gray2;
      }
    }
  }
}
</style>
