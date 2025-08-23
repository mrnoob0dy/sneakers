<script setup>
import { inject, reactive, watch, ref, onMounted } from "vue";
import CardList from "../components/CardList.vue";
import axios from "axios";
import debounce from "lodash.debounce";

const items = ref([]);
const { cartItems, addToCart, removeFromCart } = inject("cart");

const filters = reactive({
  sortBy: "title",
  searchQuery: "",
});

const onChangeSelect = event => {
  filters.sortBy = event.target.value;
};

const onChangeSearchInput = debounce(event => {
  filters.searchQuery = event.target.value;
}, 600);

const addToFavorite = async item => {
  try {
    if (!item.isFavorite) {
      const obj = {
        item_id: item.id,
      };
      item.isFavorite = true;
      const { data } = await axios.post("https://8bfe6208b79548d9.mokky.dev/favorites", obj);
      item.favoriteId = data.id;
    } else {
      item.isFavorite = false;
      await axios.delete(`https://8bfe6208b79548d9.mokky.dev/favorites/${item.favoriteId}`);
      item.favoriteId = null;
    }
  } catch (error) {
    console.log(error);
  }
};

const onClickAddPlus = item => {
  if (!item.isAdded) {
    addToCart(item);
  } else {
    removeFromCart(item);
  }
};

const fetchFavorites = async () => {
  try {
    const { data: favorites } = await axios.get(`https://8bfe6208b79548d9.mokky.dev/favorites`);
    items.value = items.value.map(item => {
      const favorite = favorites.find(favorite => favorite.item_id === item.id);
      if (!favorite) {
        return item;
      }

      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      };
    });
  } catch (error) {
    console.log(error);
  }
};

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy,
    };

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`;
    }

    const { data } = await axios.get(`https://8bfe6208b79548d9.mokky.dev/items`, { params });
    items.value = data.map(obj => ({
      ...obj,
      isFavorite: false,
      isAdded: false,
      favoriteId: null,
    }));
  } catch (error) {
    console.log(error);
  }
};

onMounted(async () => {
  const localCartItems = localStorage.getItem("cartItems");
  cartItems.value = localCartItems ? JSON.parse(localCartItems) : [];
  await fetchItems();
  await fetchFavorites();

  items.value = items.value.map(item => ({
    ...item,
    isAdded: cartItems.value.some(cartItem => cartItem.id === item.id),
  }));
});

watch(filters, fetchItems);
watch(cartItems, () => {
  items.value = items.value.map(item => ({
    ...item,
    isAdded: false,
  }));
});
</script>

<template>
  <div class="header__content">
    <h2 class="title-2">Все кроссовки</h2>

    <div class="filters-wrapper">
      <select @change="onChangeSelect" name="" id="">
        <option value="name">По названию</option>
        <option value="price">По цене (дешевые)</option>
        <option value="-price">По цене (дорогие)</option>
      </select>

      <div class="search-wrapper">
        <img src="/search.svg" alt="Search" />
        <input @input="onChangeSearchInput" class="search__input" type="text" placeholder="Поиск..." />
      </div>
    </div>
  </div>

  <CardList :items="items" @addToFavorite="addToFavorite" @addToCart="onClickAddPlus"></CardList>
</template>
