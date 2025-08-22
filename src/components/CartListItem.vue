<script setup>
import { inject } from "vue";
import CartItem from "./CartItem.vue";

const { cartItems, removeFromCart } = inject("cart");
</script>

<template>
  <div class="cart__list">
    <CartItem
      v-for="item in cartItems"
      :key="item.id"
      :title="item.title"
      :price="item.price"
      :imageUrl="item.imageUrl"
      @onClickRemove="() => removeFromCart(item)"
    />
  </div>
</template>

<style scoped lang="scss">
.cart__list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
</style>
