<template>
  <footer class="footer">
    <div class="footer__wrapper container">
      <a href="#" class="footer__logo" aria-label="Ссылка на первый блок" />
      <nav class="footer__navigation">
        <ul class="footer__nav-list">
          <li class="footer__nav-item">
            <a href="#" class="footer__nav-link">
              Каталог
            </a>
          </li>
          <li class="footer__nav-item">
            <a href="#" class="footer__nav-link">
              О нас
            </a>
          </li>
          <li class="footer__nav-item">
            <a href="#" class="footer__nav-link">
              Подбор товара
            </a>
          </li>
          <li class="footer__nav-item">
            <a href="#" class="footer__nav-link">
              Наша команда
            </a>
          </li>
          <li class="footer__nav-item">
            <a href="#" class="footer__nav-link">
              Доставка и оплата
            </a>
          </li>
          <li class="footer__nav-item">
            <a href="#" class="footer__nav-link">
              Контакты
            </a>
          </li>
        </ul>
      </nav>
      <a href="#" class="footer__link-to-top" />
    </div>
  </footer>
</template>

<script>
export default {
}
</script>

<style lang="scss">
.footer {
  display: block;
  width: 100%;
  height: 80px;
  background: #444b58;

  &__wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &__logo {
    display: inline-block;
    width: 145px;
    height: 24px;
    background-image: url("/images/logo.svg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: contain;
  }

  &__navigation {
    display: block;
    width: max-content;
  }

  &__nav-list {
    display: flex;
  }

  &__nav-item {
    display: block;
    width: max-content;

    &:not(:last-child) {
      margin-right: 40px;
    }
  }

  &__nav-link {
    font-family: "Intro Book", sans-serif;
    font-size: 14px;
    line-height: 14px;
    color: #fff;
  }

  &__link-to-top {
    display: none;
  }
}

@media screen and (max-width: 1180px) {
  .footer {
    &__navigation {
      display: none;
    }

    &__link-to-top {
      display: block;
      width: 42px;
      height: 42px;
      border-radius: 100%;
      background-image: url("/images/icons/totop.svg");
      background-repeat: no-repeat;
      background-position: center;
      background-size: 32px;
    }
  }
}
</style>
