<script setup>
import Card from "./Card.vue";

function onClickAdd() {}
</script>

<template>
  <div class="grid">
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="12999"
      image-url="/sneakers/sneakers-1.jpg"
      title="Мужские Кроссовки Nike Blazer Mid Suede"
      :onClickAdd="onClickAdd"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="12999"
      image-url="/sneakers/sneakers-2.jpg"
      title="Мужские Кроссовки Nike Air Max 270"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="8499"
      image-url="/sneakers/sneakers-3.jpg"
      title="Мужские Кроссовки Nike Blazer Mid Suede"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="8999"
      image-url="/sneakers/sneakers-4.jpg"
      title="Кроссовки Puma X Aka Boku Future Rider"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="15199"
      image-url="/sneakers/sneakers-5.jpg"
      title="Мужские Кроссовки Under Armour Curry 8"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="11299"
      image-url="/sneakers/sneakers-6.jpg"
      title="Мужские Кроссовки Nike Kyrie 7"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="10799"
      image-url="/sneakers/sneakers-7.jpg"
      title="Мужские Кроссовки Jordan Air Jordan 11"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="16499"
      image-url="/sneakers/sneakers-8.jpg"
      title="Мужские Кроссовки Nike LeBron XVIII"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="13999"
      image-url="/sneakers/sneakers-9.jpg"
      title="Мужские Кроссовки Nike Lebron XVIII Low"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="8499"
      image-url="/sneakers/sneakers-10.jpg"
      title="Мужские Кроссовки Nike Blazer Mid Suede"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="8999"
      image-url="/sneakers/sneakers-11.jpg"
      title="Кроссовки Puma X Aka Boku Future Rider"
    ></Card>
    <Card
      :is-favorite="false"
      :is-added="false"
      :price="11299"
      image-url="/sneakers/sneakers-12.jpg"
      title="Мужские Кроссовки Nike Kyrie Flytrap IV"
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
