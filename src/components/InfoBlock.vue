<script setup>
defineProps({
  title: String,
  description: String,
  imgUrl: String,
});
</script>

<template>
  <div class="info-block-wrapper">
    <img class="info-block-img" :src="imgUrl" alt="Info image" />
    <h2 class="info-block-title">{{ title }}</h2>
    <p class="info-block-description">{{ description }}</p>
  </div>
</template>

<style lang="scss" scoped>
.info-block-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: auto 0;
}

.info-block-img {
  margin-bottom: 21px;
  width: 120px;
  aspect-ratio: 1;
}

.info-block-title {
  margin-bottom: 9px;
  font-weight: 600;
  font-size: 22px;
  color: #000;
}

.info-block-description {
  font-size: 16px;
  line-height: 150%;
  text-align: center;
  color: #000;
  opacity: 0.4;
  max-width: 285px;
}
</style>
