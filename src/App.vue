<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import AppLoader from "./components/AppLoader.vue";
import { store } from "./components/store";
import axios from "axios";
export default {
  components: {
    AppHeader,
    AppMain,
    AppLoader
  },
  data() {
    return {
      store,
    };
  },
  mounted() {
    axios.get(store.apiURL).then((resp) => {
      this.store.cards = resp.data.data;
    });
  },
};
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style lang="scss">
@use "./components/styles/general.scss";
</style>

