<script lang="ts" setup></script>

<template>
  <header class="header">
    <a href="/"
      ><img class="header__logo" src="/img/logo.svg" alt="Qtim logo"
    /></a>
    <div class="header__group">
      <nav class="header__nav nav">
        <ul class="nav__list">
          <li class="nav__item"><a class="nav__link" href="#">Works</a></li>
          <li class="nav__item"><a class="nav__link" href="#">About</a></li>
        </ul>
      </nav>
      <div class="header__buttons-group">
        <button class="header__lang-button">
          <img
            class="header__lang-icon"
            src="/img/uk-lang-icon.svg"
            alt="UK flag icon"
          />
        </button>
        <a class="header__link-button" href="#">Let’s work</a>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
.header {
  height: 121px;
  margin: 0 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  &__logo {
    width: 84px;
  }

  &__group {
    display: flex;
    align-items: center;
    gap: 91px;
  }

  &__buttons-group {
    display: flex;
    gap: 16px;
  }

  &__lang-button {
    padding: 14px;
    border-radius: 999px;
    border: 2px solid $button-color;

    &:hover {
      background-color: $hover-color;
    }
  }

  &__lang-icon {
    width: 24px;
    height: 24px;
  }

  &__link-button {
    padding: 16px 32px;
    font-size: 20px;
    background-color: $text-color;
    color: $background-color;
    border-radius: 999px;
  }
}

.nav {
  &__list {
    display: flex;
    gap: 58px;
  }

  &__link {
    font-size: 20px;
  }
}
</style>
