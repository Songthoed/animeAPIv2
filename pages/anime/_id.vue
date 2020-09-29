<template>
  <div>
    <h1>{{ this.anime.name }}</h1>
    <v-row>
      <v-col md="3" cols="12">
        <img :src="this.anime.img" />
      </v-col>
      <v-col md="6" offset-md="1">
        <v-row>
          <v-card class="pa-2" outlined tile> SYSNOSIS </v-card>
        </v-row>
        <v-row>
          <v-card-subtitle
            :class="`rounded-br-xl`"
            class="pa-6 text-center grey darken-3"
          >
            {{ this.anime.synopsis }}
          </v-card-subtitle>
        </v-row>
        <v-alert color="black">
          <v-row no-gutters>
            <v-col>
              <v-card class="pa-2" outlined tile> SCORE </v-card>
            </v-col>
            <v-col>
              <v-card
                class="pa-2 text-center grey darken-3"
                outlined
                tile
                height="100%"
              >
                {{ this.anime.score }}
              </v-card>
            </v-col>
            <v-col offset-md="1">
              <v-card class="pa-2" outlined tile> RATE </v-card>
            </v-col>
            <v-col>
              <v-card
                class="pa-2 text-center grey darken-3"
                outlined
                tile
                height="100%"
              >
                {{ this.anime.rated }}
              </v-card>
            </v-col>
          </v-row>
          <v-row no-gutters>
            <v-col>
              <v-card class="pa-2" outlined tile> TYPE </v-card>
            </v-col>
            <v-col>
              <v-card
                class="pa-2 text-center grey darken-3"
                outlined
                tile
                height="100%"
              >
                {{ this.anime.type }}
              </v-card>
            </v-col>
            <v-col offset-md="1">
              <v-card class="pa-2" outlined tile> EPISODES </v-card>
            </v-col>
            <v-col>
              <v-card
                class="pa-2 text-center grey darken-3"
                outlined
                tile
                height="100%"
              >
                {{ this.anime.ep }}
              </v-card>
            </v-col>
          </v-row>
        </v-alert>
        <v-row no-gutters>
          <v-col class="text-center">
            <v-card class="pa-2" outlined tile> STARTDATE </v-card>
          </v-col>
          <v-col class="text-center">
            <v-card class="pa-2" outlined tile> ENDDATE </v-card>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col>
            <v-card class="pa-2 grey darken-3" outlined tile height="100%">
              {{ this.anime.start }}
            </v-card>
          </v-col>
          <v-col>
            <v-card class="pa-2 grey darken-3" outlined tile height="100%">
              {{ this.anime.end }}
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col class="text-center">
            <v-rating
              v-model="anime.score / 2.0"
              length="5"
              color="deep-orange "
              background-color="grey lighten-1"
              readonly="readonly"
              half-increments="halfIncrements"
            ></v-rating>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      anime: this.$route.params,
    };
  },
};
</script>

<style>
</style>