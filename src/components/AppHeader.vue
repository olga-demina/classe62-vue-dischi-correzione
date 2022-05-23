<template>
  <div>
    <header class="d-flex justify-content-between ps-3 pe-3">
      <div>
        <select class="form-select mt-3" @change="$emit('genreChanged', selectedGenre)" v-model="selectedGenre">
          <option value="">Seleziona un genere</option>
          <option v-for="(item, index) in genresList" :key="index" :value="item">{{ item }}</option>
        </select>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  name: "AppHeader",
  props: {
    genresList: Array
  },
  data() {
    return {
      selectedGenre: ""
    }
  }
};
</script>

<style lang="scss" scoped>
header {
  height: 70px;
  background-color: #2e3a46;
  line-height: 70px;
  img {
    width: 50px;
  }
}
</style>