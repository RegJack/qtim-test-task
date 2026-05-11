<script lang="ts" setup></script>

<template>
  <footer class="footer">
    <div class="footer__container">
      <p class="footer__subtitle">Is there a project?</p>
      <div class="footer__main-block">
        <p class="footer__title">Let’s work together</p>
        <div class="footer__contacts">
          <div class="footer__contact-block">
            <p class="footer__text">For all questions</p>
            <a
              class="footer__text footer__text_text-wrap_nowrap footer__text_margin-bottom_4px"
              href="tel:+79202780068"
              >+7 (920) 278—00—68</a
            >
            <a class="footer__text" href="mailto:qtim@agency.com">qtim@agency.com</a>
          </div>
          <div class="footer__contact-block">
            <p class="footer__text">Office in Russia</p>
            <p class="footer__text">139 Ruben Station Lake Drew, NM 52678</p>
            <a class="footer__button" href="#"
              ><img class="footer__button-link" src="/img/tracker-arrow.svg" alt="Arrow icon"
            /></a>
          </div>
          <div class="footer__contact-block">
            <p class="footer__text">Office in Dubai</p>
            <p class="footer__text">139 Ruben Station Lake Drew, NM 52678</p>
            <a class="footer__button" href="#"
              ><img class="footer__button-link" src="/img/tracker-arrow.svg" alt="Arrow icon"
            /></a>
          </div>
        </div>
      </div>
      <div class="footer__links">
        <div class="footer__links-group">
          <a class="footer__link" href="https://www.facebook.com/">Facebook</a>
          <a class="footer__link" href="https://www.instagram.com">Instagram</a>
          <a class="footer__link" href="https://t.me/JackFarral">Telegram</a>
        </div>
        <div class="footer__links-group">
          <a class="footer__link" href="https://www.behance.net/">Behance</a>
          <a class="footer__link" href="https://www.linkedin.com/in/genrikh-geyne">Linkedn</a>
          <a class="footer__link" href="#">Privacy Policy</a>
        </div>
      </div>
      <button class="footer__go-button">Go</button>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
.footer {
  background-color: $primary-color;

  &__container {
    position: relative;
    max-width: 1440px;
    margin: 0 auto;
    padding: 140px 112px 30px;

    @media (max-width: 920px) {
      padding: 70px 60px 30px;
    }
  }

  &__subtitle {
    font-size: 16px;
    line-height: 120%;
  }

  &__main-block {
    display: flex;
    gap: 368px;
    margin-top: 56px;

    @media (max-width: 1220px) {
      gap: 128px;
    }

    @media (max-width: 920px) {
      flex-direction: column;
      gap: 32px;
    }
  }

  &__title {
    width: fit-content;
    max-width: 464px;
    font-size: 112px;
    text-decoration: underline;
    text-decoration-thickness: 1px;
    text-underline-offset: 15px;

    @media (max-width: 480px) {
      font-size: 64px;
    }
  }

  &__contacts {
    width: 152px;
  }

  &__contact-block {
    margin-bottom: 36px;

    &:last-of-type {
      margin-bottom: 0px;
    }
  }

  &__text {
    display: block;
    line-height: 120%;

    &:first-child {
      margin-bottom: 12px;
    }

    &_text-wrap_nowrap {
      text-wrap: nowrap;
    }

    &_margin-bottom_4px {
      margin-bottom: 4px;
    }
  }

  &__button {
    display: block;
    width: 32px;
    height: 32px;
    padding: 11.5px;
    margin-top: 8px;
    background-color: $text-color;
    border-radius: 999px;
    line-height: 9px;
  }

  &__button-link {
    width: 9px;
    height: 9px;
  }

  &__links {
    margin-top: 273px;
    display: flex;
    justify-content: space-between;

    @media (max-width: 1220px) {
      margin-top: 103px;
      margin-bottom: 170px;
      gap: 32px;
      justify-content: center;
    }

    @media (max-width: 660px) {
      margin-top: 83px;
      flex-direction: column;
      align-items: center;
      gap: 16px;
    }
  }

  &__links-group {
    display: flex;
    gap: 32px;
  }

  &__link {
    font-size: 16px;
    line-height: 120%;
    text-decoration: underline;
    text-decoration-thickness: 0.4px;
    text-underline-offset: 4px;
  }

  &__go-button {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    padding: 122px 160px 25px;
    font-size: 32px;
    background-color: $text-color;
    color: $background-color;
    border-top-left-radius: 999px;
    border-top-right-radius: 999px;

    @media (max-width: 480px) {
      padding: 110px 130px 20px;
    }
  }
}
</style>
