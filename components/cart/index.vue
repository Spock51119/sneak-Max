<template>
  <div class="cart">
    <div class="cart__wrapper">
      <div class="cart__header">
        <h2 class="cart__title">
          Корзина
        </h2>
        <button class="cart__btn-close" @click="cartShow" />
      </div>
      <div class="cart__items">
        <AppItem
          v-for="(item, index) in getCartList"
          :key="item.article"
          :index="index"
          :title="item.title"
          :cost="item.cost"
          :image="item.imageLinks[0]"
        />
      </div>
      <div class="cart__footer">
        <div class="cart__total-wrap">
          <span class="cart__total-text">Итого:</span>
          <span class="cart__total-cost">25 789</span>
        </div>
        <button class="cart__order-btn">
          Перейти в корзину
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import AppItem from './item.vue'
export default {
  components: {
    AppItem
  },
  computed: {
    getCartList () {
      return this.$store.getters['data/cart']
    }
  },
  methods: {
    cartShow () {
      this.$store.commit('data/cartShow')
      document.body.classList.toggle('stop-scroll')
    }
  }
}
</script>

<style lang="scss">
.cart {
  position: absolute;
  top: 0;
  left: -3vw;
  right: 0;
  z-index: 20;
  display: flex;
  width: 103vw;
  height: 100vh;
  padding: 70px 3vw;
  background-color: #444b58a6;

  &__wrapper {
    position: absolute;
    top: 70px;
    right: 3vw;
    left: auto;
    z-index: 20;
    display: flex;
    flex-direction: column;
    width: 94vw;
    max-width: 480px;
    margin: 0 3vw;
    background-color: #fff;
    border-radius: 4px;
    overflow: hidden;
  }

  &__header {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 50px;
  }

  &__title {
    display: inline-block;
    width: max-content;
    font-family: "Intro Bold", sans-serif;
    font-style: normal;
    font-weight: bold;
    font-size: 24px;
    line-height: 35px;
    color: #444b58;
  }

  &__btn-close {
    position: absolute;
    top: 10px;
    right: 15px;
    display: block;
    width: 32px;
    height: 32px;
    background-color: rgba(246, 113, 113, 0.65);
    background-image: url("/images/icons/cross.png");
    background-repeat: no-repeat;
    background-position: center;
    background-size: 20px;
    border-radius: 100%;
    transform: rotate(45deg);
    transition: background-color 0.3s;

    &:hover {
      background-color: rgb(245, 79, 79);
      transition: background-color 0.3s;
    }
  }

  &__items {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 480px;
    height: 325px;
    overflow-y: auto;
  }

  &__footer {
    display: flex;
    justify-content: space-between;
    padding: 15px 20px;
  }

  &__total-wrap {
    display: flex;
    flex-direction: column;
  }

  &__total-text {
    margin-bottom: 10px;
    font-family: "Intro Book", sans-serif;
    font-size: 14px;
    line-height: 20px;
    color: #4d4d4d;
  }

  &__total-cost {
    font-family: "Intro Bold", sans-serif;
    font-style: normal;
    font-weight: bold;
    font-size: 20px;
    line-height: 20px;
    color: #4d4d4d;

    &::after {
      content: " ₽";
    }
  }

  &__order-btn {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 22px 47px;
    height: 50px;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #fff;
    background: #f14f4f;
    border-radius: 4px;
  }
}

@media screen and (max-width: 450px) {
  .cart {
    &__order-btn {
      padding: 0 18px;
      height: 50px;
      font-size: 14px;
    }

    &__total-cost {
      font-size: 16px;
    }
  }
}
</style>
