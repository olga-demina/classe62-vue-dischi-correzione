<template>
  <main class="container mt-5">
    <div class="row row-cols-5">
      <AppDisc
        v-for="(discItem, index) in discList"
        :key="index"
        :disc="discItem"
      />
    </div>
  </main>
</template>

<script>
// import axios from "axios";
import AppDisc from "./AppDisc";

export default {
  name: "Main",
  components: {
    AppDisc,
  },
  props: {
    discList: Array
  }
  // data() {
  //   return {
  //     discs: []
  //   }
  // },
  // created() {
  //   axios
  //     .get("https://flynn.boolean.careers/exercises/api/array/music")
  //     .then((res) => {
  //       this.discs = res.data.response;
  //     });
  // },
};
</script>

