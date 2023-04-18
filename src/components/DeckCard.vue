<script>
export default {
  name: "DeckCard",
  props: {
    cardObj: Object,
  },
};
</script>

<template>
    <div class="text-center card">
      <img :src="cardObj.card.card_images[0].image_url_small" alt="" />
        <h3>{{ cardObj.name }}</h3>
          <p>{{ cardObj.archetype }}</p>
    </div>
  </template>


<style scoped>
.card {
  background-color: #d48f38;
}
</style>