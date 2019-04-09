<template>
  <v-container>
    <v-layout align-center justify-space-around row fill-height>
      <h2>{{singleMovie.title}}</h2>
      <v-flex xs6>
        <img :src="singleMovie.Poster">
      </v-flex>
      <v-flex xs6>
        <v-list subheader three-line>
          <v-list-tile>
            <v-list-tile-content>
              <v-list-tile-title>Director</v-list-tile-title>
              <v-list-tile-sub-title>{{singleMovie.Director}}</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import axios from "axios";

export default {
  props: ["id"],
  data: () => {
    return {
      singleMovie: ""
    };
  },
  mounted() {
    axios
      .get(
        `http://www.omdbapi.com/?apikey=bf53667&i=${
          this.id
        }&Content-Type=application/json`
      )
      .then(response => {
        this.singleMovie = response.data;
      })
      .catch(error => console.log(error));
  }
};
</script>

<style>
</style>
