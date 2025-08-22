<script setup>
import Card from "./Card.vue";

defineProps({
  items: Array,
});

const emit = defineEmits(["addToFavorite", "addToCart"]);

function onClickAdd() {}
</script>

<template>
  <div class="grid">
    <Card
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :is-favorite="item.isFavorite"
      :is-added="false"
      :price="item.price"
      :image-url="item.imageUrl"
      :title="item.title"
      :onClickAdd="() => emit('addToCart', item)"
      :onClickFavorite="() => emit('addToFavorite', item)"
      :isAdded="item.isAdded"
    ></Card>
  </div>
</template>

<style scoped lang="scss">
.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px;
  padding: 0 60px;
}
</style>
