<template>
  <div class="cart__item">
    <picture>
      <source :srcset="image + 'webp'" type="image/webp">
      <source :srcset="image + 'jpg'" type="image/jpg">
      <img :src="image + 'jpg'" alt="Фотография товара" loading="lazy" class="cart__item-image">
    </picture>
    <!-- <img :src="image" alt="Фотография товара" class="cart__item-image"> -->
    <div class="cart__item-text">
      <a href="#" class="cart__item-name">
        {{ title }}
      </a>
      <span class="cart__item-cost">
        {{ cost }}
      </span>
    </div>
    <button class="cart__item-delite" @click="remove" />
  </div>
</template>

<script>
export default {
  props: ['title', 'cost', 'image', 'index'],
  methods: {
    remove () {
      this.$store.commit('data/removeProduct', this.index)
    }
  }
}
</script>

<style lang="scss">
.cart {
  &__item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 20px;
    background-color: #fff;
    transition: background-color 0.3;

    &:hover {
      background-color: #ccd9f244;
      transition: background-color 0.3;
    }

    &-image {
      display: flex;
      width: 100px;
      height: 100px;
      object-fit: contain;
      margin-right: 10px;
    }

    &-text {
      display: flex;
      flex-direction: column;
    }

    &-name {
      margin-bottom: 15px;
      font-family: "Intro Book", sans-serif;
      font-size: 14px;
      line-height: 20px;
      color: #444b58;
    }

    &-cost {
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

    &-delite {
      display: block;
      width: 32px;
      height: 32px;
      border-radius: 100%;
      background-image: url("/images/icons/trash.svg");
      background-repeat: no-repeat;
      background-position: center;
      background-size: 20px;
      background-color: transparent;
    }
  }
}

@media screen and (max-width: 450px) {
  .cart {
    &__item-image {
      width: 70px;
      height: 70px;
    }

    &__item-cost {
      font-size: 16px;
    }
  }
}
</style>
