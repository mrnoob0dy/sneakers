<script setup>
defineProps({
  id: Number,
  imageUrl: String,
  title: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function,
});
</script>

<template>
  <div class="card">
    <div class="card__images">
      <img
        v-if="onClickFavorite"
        class="card__like"
        @click="onClickFavorite"
        :src="isFavorite ? '/like-2.svg' : '/like-1.svg'"
        alt="Like"
      />
      <img class="card__sneaker" :src="imageUrl" :alt="title" />
    </div>
    <div class="card__text">
      <h3 class="card__title">{{ title }}</h3>
      <div class="card__info">
        <div class="card__price">
          <span class="card__price-text">Цена:</span>
          <span class="card__price-price">{{ price }} руб.</span>
        </div>
        <button v-if="onClickAdd" @click="onClickAdd" class="card__price-btn">
          <img :src="isAdded ? '/checked.svg' : '/plus.svg'" alt="Add to cart" />
        </button>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.card {
  max-width: 210px;
  width: 100%;
  border: 1px solid #f3f3f3;
  border-radius: 40px;
  background-color: transparent;
  padding: 35px 30px;
  transition: all 0.3s ease-in;

  &:hover {
    box-shadow: 0 14px 30px 0 rgba(0, 0, 0, 0.05);
    transform: translateY(-10px);
    background-color: white;
  }
}

.card__images {
  position: relative;
  margin-bottom: 14px;
}

.card__like {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 10;
  cursor: pointer;
}

.card__title {
  margin-bottom: 14px;
  font-size: 14px;
  color: #000;
}

.card__info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 5px;
}

.card__price {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.card__price-text {
  font-weight: 500;
  font-size: 11px;
  text-transform: uppercase;
  color: #bdbdbd;
}

.card__price-price {
  font-weight: 700;
  font-size: 14px;
  color: #000;
}
</style>
