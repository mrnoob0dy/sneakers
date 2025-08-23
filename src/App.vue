<script setup>
import { computed, provide, ref, watch } from "vue";
import Drawer from "./components/Drawer.vue";
import Header from "./components/Header.vue";

const cartItems = ref([]);
const drawerOpen = ref(false);
const totalPrice = computed(() => cartItems.value.reduce((acc, item) => acc + item.price, 0));
const vatPrice = computed(() => totalPrice.value * 0.05);

const closeDrawer = () => {
  drawerOpen.value = false;
};

const openDrawer = () => {
  drawerOpen.value = true;
};

const addToCart = item => {
  cartItems.value.push(item);
  item.isAdded = true;
};

const removeFromCart = item => {
  cartItems.value.splice(cartItems.value.indexOf(item), 1);
  item.isAdded = false;
};

watch(
  cartItems,
  () => {
    localStorage.setItem("cartItems", JSON.stringify(cartItems.value));
  },
  { deep: true }
);

provide("cart", {
  closeDrawer,
  openDrawer,
  cartItems,
  addToCart,
  removeFromCart,
});
</script>

<template>
  <Drawer v-if="drawerOpen" :totalPrice="totalPrice" :vatPrice="vatPrice" />
  <div class="wrapper">
    <Header :totalPrice="totalPrice" @open-drawer="openDrawer"></Header>
    <div class="content-wrapper">
      <RouterView />
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
