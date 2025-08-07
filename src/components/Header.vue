<template>
  <header class="header">
    <div class="header__left">
      <img src="/logo.png" alt="Logo" width="40" height="40" />
      <div class="header__text">
        <h2 class="header__title">Vue Sneakers</h2>
        <p class="header__description">Магазин лучших кроссовок</p>
      </div>
    </div>
    <ul class="nav">
      <li class="nav__item">
        <img src="/cart.svg" alt="Cart" />
        <span class="cart">1205 руб.</span>
      </li>
      <li class="nav__item">
        <img src="/heart.svg" alt="Heart" />
        <span>Закладки</span>
      </li>
      <li class="nav__item">
        <img src="/profile.svg" alt="Profile" />
        <span>Профиль</span>
      </li>
    </ul>
  </header>
</template>

<style scoped lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 40px;
  border-bottom: 1px solid #eaeaea;
  padding: 0 60px 44px;
  margin-bottom: 45px;
}

.header__left {
  display: flex;
  align-items: center;
  gap: 16px;
}

.header__text {
  display: flex;
  flex-direction: column;
}

.header__title {
  font-weight: 700;
  font-size: 20px;
  text-transform: uppercase;
  color: #000;
}

.header__description {
  font-size: 14px;
  color: #9d9d9d;
}

.nav {
  display: flex;
  align-items: center;
  gap: 32px;
}

.nav__item {
  display: flex;
  align-items: center;
  gap: 9px;
  cursor: pointer;

  span {
    font-weight: 400;
    font-size: 14px;
    color: #5c5c5c;
    transition: color 0.3s ease;
  }

  .cart {
    font-weight: 600;
    font-size: 14px;
    color: #5c5c5c;
  }

  &:hover {
    span {
      color: black;
    }
  }
}
</style>
