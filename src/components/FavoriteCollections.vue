<script>
import axios from "axios";
import Card from "./card.vue";

export default {
  components: { Card },

  data() {
    return {
      showsData: "",
      showObj: {},
      filteredShowData: [],
      favorites: [
        {
          id: 100,
          name: "Blue Bloods",
          image:
            "https://static.tvmaze.com/uploads/images/original_untouched/361/903737.jpg",
          summary:
            "<p><b>Blue Bloods </b>is a drama about a multi-generational family of cops dedicated to New York City law enforcement. Frank Reagan is the New York Police Commissioner and heads both the police force and the Reagan brood. He runs his department as diplomatically as he runs his family, even when dealing with the politics that plagued his unapologetically bold father, Henry, during his stint as Chief. A source of pride and concern for Frank is his eldest son Danny, a seasoned detective, family man and Iraq War vet who on occasion uses dubious tactics to solve cases with his loyal and tough partner, Detective Jackie Curatola. The Reagan women in the family include Erin, a N.Y. Assistant D.A., who also serves as the legal compass for her siblings and father, and single parent to her teenage daughter Nicky; and Linda, Danny's supportive wife. Jamie is the youngest Reagan, a recent grad of Harvard Law and the family's \"golden boy.\" Unable to deny the family tradition, Jamie has decided to give up a lucrative future in law and follow in the family footsteps as a cop.</p>",
        },
        {
          id: 200,
          name: "The Tomorrow People",
          image:
            "https://static.tvmaze.com/uploads/images/original_untouched/55/138044.jpg",
          summary:
            "<p>They are the next evolutionary leap of mankind, a generation of humans born with paranormal abilities - <b>The Tomorrow People</b>. Stephen Jameson stands at the crossroads between the world we know and the shifting world of the future. Up until a year ago, Stephen was a \"normal\" teenager - until he began hearing voices and teleporting in his sleep, never knowing where he might wake up. Now, Stephen's issues have gone far beyond the usual teenage angst, and he is beginning to question his sanity. In desperation, Stephen decides to listen to one of the voices in his head, and it leads him to his first encounter with the Tomorrow People - John, Cara and Russell - a genetically advanced race with the abilities of telekinesis, teleportation and telepathic communication. The Tomorrow People are being hunted down by a paramilitary group of scientists known as Ultra. Led by Dr. Jedikiah Price, Ultra sees the Tomorrow People as a very real existential threat from a rival species, and the outcast group has been forced to hide out in an abandoned subway station just beneath the surface of the human world. Trading in secrets, Jedikiah offers Stephen the chance for a normal life with his family and best friend, Astrid, if he will help in the struggle to isolate and eradicate the Tomorrow People. On the other hand, Cara, John and Russell offer Stephen a different type of family and a home where he truly belongs. Unwilling to turn his back on humanity or the world of the Tomorrow People, Stephen sets out on his own path - a journey that could take him into the shadowy past to uncover the truth about his father's mysterious disappearance, or into an unknown future with The Tomorrow People.</p>",
        },
        {
          id: 220,
          name: "Crossing Lines",
          image:
            "https://static.tvmaze.com/uploads/images/original_untouched/231/577869.jpg",
          summary:
            "<p>The series taps into a fictional unit mandated by the International Criminal Court (ICC) to investigate cross-border crimes and ultimately bring global criminals to justice. <b>Crossing Lines</b> is set in the world's most exotic locales, where an elite team of eager cops work to solve the most notorious international crimes.</p>",
        },
      ],
      name: "",
      errors: [],
      isInputHasValue: false,
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
    iterate(obj) {
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
            (show) =>
              !show.name.toLowerCase().indexOf(this.name.toLowerCase())
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
            <div class="col-md-3 col-sm-12 mt-sm-3 mb-sm-3">
              <form class="form-inline">
                <input
                  class="form-control mr-sm-2 search"
                  type="search"
                  placeholder="Search"
                  aria-label="Search"
                  v-model="name"
                  @keyup="checkInputTyping"
                />
                <div class="searchResult" v-if="isInputHasValue">
                  <ul>
                    <li
                      v-for="show in filterShows"
                      :key="show.id"
                      @click="getIdFromList(show.id)"
                    >
                      {{ show.name }} {{ show.id }}
                    </li>
                  </ul>
                </div>
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
