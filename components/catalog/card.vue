<template>
  <div
    class="catalog__card-item card"
  >
    <div class="card__btns">
      <button class="card__product-link card__btn" aria-label="open product page" @click="openProduct" />
      <button class="card__to-cart card__btn" aria-label="add to cart" @click="addToCart" />
    </div>
    <picture>
      <source srcset="/images/nike.webp" type="image/webp">
      <source srcset="/images/nike.jpg" type="image/jpg">
      <img src="/images/nike.jpg" alt="Кросовок" loading="lazy" class="card__image">
    </picture>
    <h3 class="card__name">
      {{ title }}
    </h3>
    <span class="card__cost">
      {{ cost }}
    </span>
  </div>
</template>
<script>
export default {
  props: ['id', 'title', 'cost'],
  computed: {
    product () {
      return this.$store.getters['data/products'][this.id]
    }
  },
  methods: {
    addToCart () {
      this.$store.commit('data/setProduct', {
        id: this.id,
        ...this.$store.getters['data/products'][this.id]
      })
    },
    openProduct () {
      this.$store.commit('data/productShow')
      this.$store.commit('data/setCurrentId', this.id)
      document.body.classList.toggle('stop-scroll')
    }
  }
}
</script>
<style lang="scss">
$gray: #b2b5bb;
$text: #444b58;

.card {
  position: relative;
  display: grid;
  grid-template-rows: 1fr auto auto;

  &__image {
    position: relative;
    z-index: 1;
    grid-area: 1/1/2/2;
    height: auto;
    width: 100%;
    object-fit: cover;
  }

  &__btns {
    position: absolute;
    z-index: 2;
    grid-area: 1/1/2/2;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.6);
    border-radius: 4px;
    opacity: 0;
    transition: opacity 0.4s;
    transition-delay: 0.2s;
  }

  &:hover &__btns {
    opacity: 1;
    transition: opacity 0.4s;
    transition-delay: 0.2s;
  }

  &__btn {
    width: 80px;
    height: 80px;
    background-color: $text;
    border-radius: 100%;
    background-repeat: no-repeat;
    background-position: center;
    background-size: 30px;
    cursor: pointer;
  }

  &__product-link {
    margin-right: 40px;
    background-image: url("/images/icons/view.svg");
  }

  &__to-cart {
    background-image: url("/images/icons/cart.svg");
  }

  &__name {
    margin: 10px 0;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: $text;
  }

  &__cost {
    display: block;
    font-family: "Intro Regular", sans-serif;
    font-size: 20px;
    line-height: 20px;
    color: $text;

    &::after {
      content: "р";
    }
  }
}

@media screen and (max-width: 880px) {
  .card {
    &__btn {
      width: 42px;
      height: 42px;
      background-size: 28px;
    }

    &__product-link {
      margin-right: 25px;
    }
  }
}
</style>
