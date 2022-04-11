<script>
import axios from "axios";
import { ref } from "vue";
import favoritesData from "./../module/favoritesData.json";
import Card from "./Card.vue";
import SearchCollections from "./SearchCollections.vue";
export default {
  components: { Card, SearchCollections },

  data() {
    return {
      name: ref(""),
      showsData: "",
      errors: [],
      showObj: {},
      filteredShowData: [],
      favorites: favoritesData,
      isShowInFavorites: function (id) {
        return this.favorites.some(function (el) {
          return el.id === id;
        });
      },
    };
  },
  mounted() {
    axios
      .get("https://api.tvmaze.com/shows")
      .then((response) => {
        this.iterate(response.data);
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
  computed: {
    filterShows: function () {
      return this.filterShowsByName(this.filteredShowData);
    },
  },
  methods: {
    iterate: function (obj) {
      obj.forEach((show) => {
        var showItem = {};
        showItem.name = show.name;
        showItem.id = show.id;
        showItem.image = show.image.original;
        showItem.summary = show.summary;
        this.filteredShowData.push(showItem);
      });
    },
    filterShowsByName: function (shows) {
      return this.name
        ? shows.filter(
            (show) => !show.name.toLowerCase().indexOf(this.name.toLowerCase())
          )
        : shows;
    },
    checkInputTyping: function () {
      if (this.name !== "") {
        this.isInputHasValue = true;
      } else {
        this.isInputHasValue = false;
      }
    },
    getIdFromList: function (id) {
      let data = this.filteredShowData;

      let selected = data.filter(function (show) {
        return show.id === id;
      });

      if (!this.isShowInFavorites(id)) {
        this.favorites.push(...selected);
      } else {
        this.favorites;
      }
    },
  },
};
</script>

<template>
  <section class="container-fluid grayBg">
    <div class="container">
      <div class="row mt-5 pt-5">
        <div class="col-md-12 mb-4">
          <div class="row d-flex justify-content-between border-bottom">
            <div class="col-md-9 col-sm-12">
              <h2>Collect your favorites</h2>
            </div>
            <div class="col-md-3 col-sm-12 mt-sm-3 mb-sm-3 mt-md-0">
              <SearchCollections
                v-model="name"
                :filterShows="filterShows"
                :getIdFromList="getIdFromList"
              />
            </div>
          </div>
        </div>
        <div class="col-md-12">
          <div class="row">
            <Card
              v-for="(show, index) in favorites"
              :key="show.id"
              :name="show.name"
              :image="show.image"
              :summary="show.summary"
              @remove="favorites.splice(index, 1)"
            ></Card>
          </div>
        </div>
      </div>
    </div>
  </section>
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

@media (min-width: 375px) and (max-width: 767px) {
  .mt-sm-3 {
    margin-top: 16px;
  }
  .mb-sm-3 {
    margin-bottom: 16px;
  }
}
@media (min-width: 768px) and (max-width: 1024px) {
}
</style>
