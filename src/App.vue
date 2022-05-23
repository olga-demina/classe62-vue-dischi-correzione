<template>
  <div id="app">
    <AppHeader :genresList="genres" @genreChanged="saveGenre($event)" />
    <AppMain :discList="filteredDiscs" />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      discs: [],
      genres: [],
      selectedGenre: "",
    };
  },
  computed: {
    filteredDiscs() {
      // La funzione che filtra i dischi in base al genere selezionato
      let filteredDiscs = [];
      if (this.selectedGenre === "") {
        filteredDiscs = this.discs;
      } else {
        filteredDiscs = this.discs.filter((item) => {
          return item.genre === this.selectedGenre;
        });
      }
      return filteredDiscs;
    },
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        console.log(resp);
        this.discs = resp.data.response;
        // scorro array, per ogni elemento:
        // se il genere del disco corrente non è ancora nell'array di generi
        // lo pusho all'interno dell'array di generi
        this.discs.forEach((item) => {
          if (!this.genres.includes(item.genre)) {
            this.genres.push(item.genre);
          }
        });
      });
  },
  methods: {
    saveGenre(newGenre) {
      this.selectedGenre = newGenre;
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";
</style>
