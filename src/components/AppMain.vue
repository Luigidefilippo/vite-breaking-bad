<script>
import DeckCard from "./DeckCard.vue";
import { store } from "./store";
import AppLoader from "./AppLoader.vue";
export default {
  name: "AppMain",
  components: {
    DeckCard,
    AppLoader,
  },
  data() {
    return {
      store,
    };
  },
};
</script>



<template>
  <main>
    <div class="container p-5">
      <select class="form-select" aria-label="Select type">
        <option value="1">Alien</option>
        <option value="2">Ally of Justice</option>
        <option value="3"> Ancient Gear</option>
      </select>
      <div class="container-fluid p-5">
        <div class="row row-cols-5">
          <div class="col" v-for="card in store.cards">
            <DeckCard class="card" :card="card" />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>



<style scoped lang="scss">
.container {
  width: 100%;
  height: calc(100vh - 70px);
  height: 100%;
  background-color: #d48f38;
  .container-fluid {
    background-color: white;
  }
}
</style>