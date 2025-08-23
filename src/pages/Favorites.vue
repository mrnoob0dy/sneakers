<script setup>
import axios from "axios";
import { onMounted, ref } from "vue";
import CardList from "../components/CardList.vue";

const favorites = ref([]);

onMounted(async () => {
  try {
    const { data } = await axios.get("https://8bfe6208b79548d9.mokky.dev/favorites?_relations=items");
    favorites.value = data.map(obj => obj.item);
  } catch (error) {
    console.log(error);
  }
});
</script>

<template>
  <div class="favorites">
    <h2 class="title-2">Мои закладки</h2>

    <CardList :items="favorites" is-favorites></CardList>
  </div>
</template>

<style scoped lang="scss">
.title-2 {
  margin-bottom: 30px;
  padding: 0 60px;
  font-weight: 700;
  font-size: 32px;
  color: #000;
}
</style>
