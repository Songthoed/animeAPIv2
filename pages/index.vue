<template>
  <div>
    <v-text-field
      v-model="search"
      label="InsertAnimeName"
      color="gray"
      outlined
    ></v-text-field>
    <v-btn small @click="searchData()">search</v-btn>
    <div>
      <v-card
        class="mx-auto rounded-lg"
        max-width="750"
        v-for="anime in animelist"
        :key="anime.mal_id"
      >
        <v-alert outlined border="bottom">
          <v-row align="center">
            <v-col md="3">
              <v-img
                class="white--text align-end"
                height="100%"
                :src="anime.image_url"
              >
              </v-img>
            </v-col>
            <v-col md="6" offset-md="2" justify="start" align="start">
              <v-card-title class="pb-0"
                ><h3>{{ anime.title }}</h3></v-card-title
              >
              <v-card-text class="text--primary">
                Rated : {{ anime.rated }}
                <br />
                Population :
                <v-rating
                  v-model="anime.score / 2.0"
                  length="5"
                  color="deep-orange "
                  background-color="grey lighten-1"
                  readonly="readonly"
                  half-increments="halfIncrements"
                ></v-rating>
              </v-card-text>
              <v-card-actions>
                <v-btn
                  color="orange"
                  text
                  :to="{
                    name: 'anime-id',
                    params: {
                      name: anime.title,
                      img: anime.image_url,
                      synopsis: anime.synopsis,
                      score: anime.score,
                      type: anime.type,
                      start: anime.start_date,
                      end: anime.end_date,
                      rated: anime.rated,
                      ep: anime.episodes,
                    },
                  }"
                  >Explore</v-btn
                >
              </v-card-actions>
            </v-col>
          </v-row>
        </v-alert>
      </v-card>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      animelist: null,
      search: "",
    };
  },
  methods: {
    searchData() {
      axios
        .get("https://api.jikan.moe/v3/search/anime?q=" + this.search)
        .then((response) => {
          this.animelist = response.data.results.slice(0, 25);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style>
</style>