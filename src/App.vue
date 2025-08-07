<script setup>
import Header from "./components/Header.vue";
</script>

<template>
  <div class="wrapper">
    <Header></Header>
  </div>
</template>

<style lang="scss">
body {
  font-family: sans-serif;
  font-weight: 400;
  background-color: #e7f6ff;
}

.wrapper {
  margin: 85px auto;
  max-width: 80%;
  width: 100%;
  box-shadow: 0 10px 20px 0 rgba(0, 0, 0, 0.04);
  background: #fff;
  border-radius: 20px;
  padding: 45px 0;
}
</style>
