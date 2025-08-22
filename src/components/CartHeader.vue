<script setup>
import { inject } from "vue";

const { closeDrawer } = inject("cart");
</script>

<template>
  <div class="cart__header" @click="closeDrawer">
    <svg width="16" height="14" viewBox="0 0 16 14" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M1 7H14.7143" stroke="" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
      <path
        d="M8.71436 1L14.7144 7L8.71436 13"
        stroke=""
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
      />
    </svg>
    <h2 class="cart__title">Корзина</h2>
  </div>
</template>

<style scoped lang="scss">
.cart__header {
  cursor: pointer;
  margin-bottom: 30px;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  svg {
    transform: rotate(180deg);
    stroke: #9dd458;
    transition: 0.3s ease;
  }

  &:hover {
    svg {
      translate: -5px;
    }
  }
}

.cart__title {
  display: flex;
  font-weight: 700;
  font-size: 24px;
  color: #000;
}
</style>
