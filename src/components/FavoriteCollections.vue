<script>
import axios from "axios";
import Card from "./card.vue";
export default {
  components: { Card },

  data() {
    return {
      showsData: null,
      showObj: {},
      filteredShowArray: [],
      favorites: [
        {
          id: 7,
          name: "Homeland",
          image:
            "https://static.tvmaze.com/uploads/images/medium_portrait/230/575652.jpg",
          summary:
            "<p>The winner of 6 Emmy Awards including Outstanding Drama Series, <b>Homeland</b> is an edge-of-your-seat sensation. Marine Sergeant Nicholas Brody is both a decorated hero and a serious threat. CIA officer Carrie Mathison is tops in her field despite being bipolar. The delicate dance these two complex characters perform, built on lies, suspicion, and desire, is at the heart of this gripping, emotional thriller in which nothing short of the fate of our nation is at stake.</p>",
        },
        {
          id: 139,
          name: "Girls",
          image:
            "https://static.tvmaze.com/uploads/images/medium_portrait/31/78286.jpg",
          summary:
            "<p>This Emmy winning series is a comic look at the assorted humiliations and rare triumphs of a group of girls in their 20s.</p>",
        },
        {
          id: 148,
          name: "Web Therapy",
          image:
            "https://static.tvmaze.com/uploads/images/medium_portrait/0/2036.jpg",
          summary:
            "<p>Fiona Wallice is a therapist with little patience for her patients. Tired of hearing about people's problems for fifty long minutes, she devises a new treatment, the three-minute video chat. And still, the sessions end up being largely about her. If she's your therapist, you've got problems. Emmy Award® winner Lisa Kudrow co-created, produces and stars in this outrageous therapeutic send-up. Originally produced as webisodes, <b>Web Therapy</b> features an A-list guest cast who, along with Kudrow, improvise their performances with hilarious results.</p>",
        },
      ],
      search: "",
      errors: [],
    };
  },
  methods: {
    iterate(obj) {
      obj.forEach((show) => {
        var showItem = {};
        showItem.name = show.name;
        showItem.id = show.id;
        showItem.image = show.image.medium;
        showItem.summary = show.summary;
        this.filteredShowArray.push(showItem);
      });
    },
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
  computed() {
    searchShows = function () {
      return this.filteredShowArray.filter((show) => {
        let x = show.name.match(this.search);
        console.log(x);
        return x;
      });
    };
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
            <div class="col-md-3 col-sm-12 mt-sm-3 mb-sm-3">
              <form class="form-inline">
                <input
                  class="form-control mr-sm-2 search"
                  type="search"
                  placeholder="Search"
                  aria-label="Search"
                  v-model="search"
                />
              </form>
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
