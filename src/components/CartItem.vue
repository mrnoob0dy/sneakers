<script setup>
const emit = defineEmits(["onClickRemove"]);

defineProps({
  id: Number,
  imageUrl: String,
  title: String,
  price: Number,
});
</script>

<template>
  <div class="cart__item">
    <img :src="imageUrl" :alt="title" class="cart__item-img" />
    <div class="cart__item-text">
      <h3 class="cart__item-title">{{ title }}</h3>
      <span class="cart__item-price">{{ price }} руб.</span>
    </div>
    <button class="cart__item-btn">
      <img @click="() => emit('onClickRemove')" src="/close.svg" alt="Close" />
    </button>
  </div>
</template>

<style scoped lang="scss">
.cart__item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 5px;
  border: 1px solid #f3f3f3;
  border-radius: 20px;
  padding: 20px;
}

.cart__item-img {
  width: 70px;
  aspect-ratio: 1;
}

.cart__item-text {
  max-width: 150px;
}

.cart__item-title {
  margin-bottom: 8px;
  font-weight: 400;
  font-size: 14px;
  color: #000;
}

.cart__item-price {
  font-weight: 700;
  font-size: 14px;
  color: #000;
}

.cart__item-btn {
  align-self: flex-end;
}
</style>
