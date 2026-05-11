<script lang="ts" setup>
const isBurgerOpen = ref(false)

const isMobile = ref<boolean>()

const updateWidth = () => {
  isMobile.value = window.innerWidth < 620
}

onMounted(() => {
  isMobile.value = window.innerWidth < 620
  window.addEventListener('resize', updateWidth)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateWidth)
})
</script>

<template>
  <header class="header">
    <a href="/"><img class="header__logo" src="/img/logo.svg" alt="Qtim logo" /></a>
    <div class="header__group" :class="{ 'header__burger-group': isBurgerOpen && isMobile }">
      <nav class="header__nav nav">
        <ul class="nav__list">
          <li class="nav__item"><a class="nav__link" href="#">Works</a></li>
          <li class="nav__item"><a class="nav__link" href="#">About</a></li>
        </ul>
      </nav>
      <div class="header__buttons-group">
        <button class="header__lang-button">
          <img class="header__lang-icon" src="/img/uk-lang-icon.svg" alt="UK flag icon" />
        </button>
        <a class="header__link-button" href="#">Let’s work</a>
      </div>
    </div>
    <button class="header__burger-button" @click="isBurgerOpen = !isBurgerOpen">
      <svg width="36px" height="36px" viewBox="0 0 24 24" fill="none">
        <path d="M4 18L20 18" stroke="#000000" stroke-width="2" stroke-linecap="round" />
        <path d="M4 12L20 12" stroke="#000000" stroke-width="2" stroke-linecap="round" />
        <path d="M4 6L20 6" stroke="#000000" stroke-width="2" stroke-linecap="round" />
      </svg>
    </button>
  </header>
</template>

<style lang="scss" scoped>
.header {
  position: relative;
  max-width: 1440px;
  height: 121px;
  padding: 0 40px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;

  @media (max-width: 620px) {
    height: 71px;
    padding: 0 2 0px;
  }

  &__logo {
    width: 84px;
  }

  &__group {
    display: flex;
    align-items: center;
    gap: 91px;

    @media (max-width: 740px) {
      gap: 48px;
    }

    @media (max-width: 620px) {
      display: none;
    }
  }

  &__burger-group {
    position: absolute;
    z-index: 999;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 32px;
    background-color: $background-color;
  }

  &__buttons-group {
    display: flex;
    gap: 16px;

    // @media (max-width: 620px) {
    //   flex-direction: column;
    // }
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

  &__burger-button {
    display: none;

    @media (max-width: 620px) {
      display: inline-block;
    }
  }
}

.nav {
  @media (max-width: 620px) {
    width: 100%;
  }

  &__list {
    display: flex;
    gap: 58px;

    @media (max-width: 620px) {
      flex-direction: column;
      gap: 24px;
    }
  }

  &__link {
    font-size: 20px;

    @media (max-width: 620px) {
      display: block;
      width: 100%;
      text-align: center;
    }
  }
}
</style>
