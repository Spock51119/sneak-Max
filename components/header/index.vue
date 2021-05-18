<template>
  <header class="header">
    <div class="header__wrapper container">
      <AppCart v-if="openCart" />
      <a href="#" class="header__logo" />
      <nav class="header__nav">
        <ul :class="['header__nav-list', {'header__nav-list_open': openMenu}]">
          <li class="header__nav-item" @click="toggleMenu">
            <a href="#catalog" class="header__nav-link">
              Каталог
            </a>
          </li>
          <li class="header__nav-item" @click="toggleMenu">
            <a href="#about" class="header__nav-link">
              О нас
            </a>
          </li>
          <li class="header__nav-item" @click="toggleMenu">
            <a href="#quiz" class="header__nav-link">
              Подбор товара
            </a>
          </li>
          <li class="header__nav-item" @click="toggleMenu">
            <a href="#team" class="header__nav-link">
              Наша команда
            </a>
          </li>
          <li class="header__nav-item" @click="toggleMenu">
            <a href="#ask" class="header__nav-link">
              FAQ
            </a>
          </li>
          <li class="header__nav-item" @click="toggleMenu">
            <a href="#contacts" class="header__nav-link">
              Контакты
            </a>
          </li>
          <li class="header__nav-item" @click="toggleMenu">
            <button class="header__cart-btn" @click="cartShow">
              Корзина
              <span class="header__cart-btn_count">
                {{ countProducts }}
              </span>
            </button>
          </li>
        </ul>
      </nav>
      <AppBurger :open-menu="openMenu" @clickBurger="toggleMenu" />
    </div>
  </header>
</template>
<script>
import AppBurger from './burger.vue'
import AppCart from '~/components/cart/index.vue'
export default {
  components: {
    AppBurger,
    AppCart
  },
  data () {
    return {
      openMenu: false
    }
  },
  computed: {
    countProducts () {
      return this.$store.getters['data/cart'].length
    },
    openCart () {
      return this.$store.getters['data/openCart']
    }
  },
  methods: {
    toggleMenu () {
      if (document.documentElement.clientWidth < 1180) {
        document.body.classList.toggle('stop-scroll')
        this.openMenu = !this.openMenu
      }
    },
    cartShow () {
      this.$store.commit('data/cartShow')
      document.body.classList.toggle('stop-scroll')
    }
  }
}
</script>
<style lang="scss">
.header {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 100%;

  &__wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.5);
  }

  &__logo {
    display: block;
    width: 145px;
    height: 24px;
    background-image: url("/images/logo.svg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: contain;
  }

  // &__nav {
  // }

  &__nav-list {
    display: flex;
  }

  &__nav-item {
    &:not(:last-child) {
      margin-right: 40px;
    }
  }

  &__nav-link {
    color: #fff;
  }

  &__cart-btn {
    position: relative;
    background-color: transparent;
    padding-right: 30px;
    margin-right: 8px;
    color: #fff;
    background-image: url("/images/icons/cart.svg");
    background-repeat: no-repeat;
    background-position: right center;

    &_count {
      position: absolute;
      right: -8px;
      bottom: -8px;
      display: inline-block;
      font-size: 14px;
      line-height: 16px;
      align-items: center;
      width: 16px;
      height: 16px;
      background-color: #f14f4f;
      border-radius: 100%;
    }
  }
}

@media screen and (max-width: 1180px) {
  .header {
    &__wrapper {
      position: relative;
    }

    &__nav-list {
      position: absolute;
      left: -3vw;
      top: 64px;
      z-index: 20;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      width: 102vw;
      height: calc(100vh - 64px);
      max-height: 0;
      overflow: hidden;
      background-color: #484283;
      transition: max-height 0.5s;

      &_open {
        max-height: 140vh;
        border-bottom: 2px solid #0e074e;
        transition: max-height 0.5s;
      }
    }

    &__nav-item {
      line-height: 32px;

      &:not(:last-child) {
        margin-right: 0;
        margin-bottom: 20px;
      }
    }
  }
}
</style>
