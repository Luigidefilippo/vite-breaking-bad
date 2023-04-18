<script>
import DeckCard from "./DeckCard.vue";
import { store } from "./store";
import AppLoader from "./AppLoader.vue";
import axios from "axios";
export default {
  name: "AppMain",
  components: {
    DeckCard,
    AppLoader,
  },
  data() {
    return {
      store,
      selectedOptions: ["Alien", "Ally, of Justice", "Ancient Gear"],
      cardsFounded: 0,
      selectedArchetype: "",
    };
  },
  methods: {
    getArchetype() {
      store.loader = true;
      if (this.selectedArchetype) {
        axios
          .get(store.apiURL, {
            params: {
              archetype: this.selectedArchetype,
            },
          })
          .then((resp) => {
            this.store.cards = resp.data.data;
            this.cardsFounded = resp.data.meta.current_rows;
            store.loading = false;
          });
      } else {
        this.getCard();
      }
    },
    getCard() {
      axios.get(store.apiURL).then((resp) => {
        this.store.cards = resp.data.data;
        this.cardsFounded = resp.data.meta.current_rows;
      });
    },
  },
};
</script>



<template>
  <main>
    <div class="container p-5">
      <div class="container-fluid p-5">
        <select
          class="form-select"
          name="option"
          id="option"
          v-model="selectedArchetype"
          @change="getArchetype">

          <option value="">All</option>
          <option v-for="option in selectedOptions" :value="option">
            {{ option }}
          </option>
        </select>
        <h3 class="found p-2">
          Found <span>{{ cardsFounded }}</span> cards
        </h3>
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
  height: 100%;
  background-color: #d48f38;
  .container-fluid {
    background-color: white;
  }
}
</style>