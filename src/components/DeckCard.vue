<script>
export default {
  name: "DeckCard",
  props: {
    card: Object,
  },
};
</script>

<template>
    <div class="text-center card">
      <img :src="card.card_images[0].image_url_small" alt="" />
        <h3>{{ card.name }}</h3>
          <p>{{ card.archetype }}</p>
    </div>
  </template>


<style scoped>
.card {
  background-color: #d48f38;
}
</style>