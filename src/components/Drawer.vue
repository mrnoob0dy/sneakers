<script setup>
import CartHeader from "./CartHeader.vue";
import CartListItem from "./CartListItem.vue";
import InfoBlock from "./InfoBlock.vue";

const emit = defineEmits(["createOrder"]);

defineProps({
  totalPrice: Number,
  vatPrice: Number,
  cartButtonDisabled: Boolean,
});
</script>

<template>
  <div class="drawer"></div>
  <div class="cart">
    <CartHeader />

    <InfoBlock
      v-if="!totalPrice"
      title="Корзина пустая"
      description="Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ."
      img-url="/package-icon.png"
    />

    <CartListItem />

    <div v-if="totalPrice" class="cart__info">
      <div class="cart__info-item">
        <span class="cart__info-title">Итого:</span>
        <div class="cart__info-border"></div>
        <span class="cart__info-total">{{ totalPrice }} руб.</span>
      </div>
      <div class="cart__info-item">
        <span class="cart__info-title">Налог 5%:</span>
        <div class="cart__info-border"></div>
        <span class="cart__info-tax">{{ vatPrice }} руб.</span>
      </div>
      <button @click="() => emit('createOrder')" :disabled="cartButtonDisabled" class="cart__info-btn">
        Оформить заказ
      </button>
    </div>
  </div>
</template>

<style scoped lang="scss">
.drawer {
  position: fixed;
  inset: 0;
  z-index: 15;
  background-color: rgba(0, 0, 0, 0.5);
}

.cart {
  width: 385px;
  position: fixed;
  right: 0;
  top: 0;
  z-index: 20;
  display: flex;
  flex-direction: column;
  height: 100%;
  box-shadow: -10px 4px 24px 0 rgba(0, 0, 0, 0.1);
  background-color: #fff;
  padding: 30px;
}

.cart__info {
  margin-top: auto;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.cart__info-item {
  display: flex;
  gap: 8px;
}

.cart__info-title {
  font-weight: 400;
  font-size: 16px;
  color: #000;
}

.cart__info-border {
  border-bottom: 1px dashed #dfdfdf;
  flex-grow: 1;
  translate: 0 -3px;
}

.cart__info-total {
  font-weight: 600;
  font-size: 16px;
  color: #000;
}

.cart__info-tax {
  font-weight: 600;
  font-size: 16px;
  color: #000;
}

.cart__info-btn {
  margin-top: 4px;
  font-weight: 600;
  font-size: 16px;
  text-align: center;
  color: #fff;
  padding: 20px;
  background-color: #9dd458;
  border-radius: 18px;
  transition: all 0.3s ease;

  &:hover {
    background-color: #28410a;
  }

  &:disabled {
    background-color: gray;
  }
}
</style>
