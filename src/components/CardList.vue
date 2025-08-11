<script setup>
import Card from "./Card.vue";

defineProps({
  items: Array,
});

function onClickAdd() {}
</script>

<template>
  <div class="grid">
    <Card
      v-for="item in items"
      :key="item.id"
      :is-favorite="false"
      :is-added="false"
      :price="item.price"
      :image-url="item.imageUrl"
      :title="item.title"
      :onClickAdd="onClickAdd"
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
