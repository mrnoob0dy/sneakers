<script setup>
import CartItem from "./CartItem.vue";
</script>

<template>
  <div class="cart__list">
    <CartItem />
    <CartItem />
    <CartItem />
  </div>
</template>

<style scoped lang="scss">
.cart__list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
</style>
