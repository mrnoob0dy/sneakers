<script setup>
import CardList from "./components/CardList.vue";
import Drawer from "./components/Drawer.vue";
import Header from "./components/Header.vue";
</script>

<template>
  <!-- <Drawer /> -->
  <div class="wrapper">
    <Header></Header>
    <div class="content-wrapper">
      <div class="header__content">
        <h2 class="title-2">Все кроссовки</h2>

        <div class="filters-wrapper">
          <select name="" id="">
            <option value="">По названию</option>
            <option value="">По цене (дешевые)</option>
            <option value="">По цене (дорогие)</option>
          </select>

          <div class="search-wrapper">
            <img src="/search.svg" alt="Search" />
            <input class="search__input" type="text" placeholder="Поиск..." />
          </div>
        </div>
      </div>

      <CardList></CardList>
    </div>
  </div>
</template>

<style lang="scss">
body {
  font-family: sans-serif;
  font-weight: 400;
  background-color: #e7f6ff;
  padding: 85px 0;
}

.wrapper {
  margin: 0 auto;
  max-width: 1080px;
  width: 100%;
  box-shadow: 0 10px 20px 0 rgba(0, 0, 0, 0.04);
  background: #fff;
  border-radius: 20px;
  padding: 45px 0;
}

.title-2 {
  font-weight: 700;
  font-size: 32px;
  color: #000;
}

.header__content {
  margin-bottom: 30px;
  padding: 0 60px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
}

.filters-wrapper {
  display: flex;
  align-items: center;
  gap: 10px;
}

.search-wrapper {
  position: relative;

  img {
    position: absolute;
    top: 50%;
    left: 18px;
    transform: translateY(-50%);
  }
}

.search__input {
  padding: 15px 18px;
  padding-left: 46px;
  border: 1px solid #f3f3f3;
  border-radius: 10px;
  background-color: #fff;
  width: 250px;
  color: #000;

  &::placeholder {
    font-weight: 400;
    font-size: 14px;
    color: #c4c4c4;
  }

  &:focus {
    border-color: #a5d364;
  }
}
</style>
