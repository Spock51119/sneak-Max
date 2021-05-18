<template>
  <section class="product">
    <div class="product__wrapper container">
      <AppImages
        v-if="width && width > 770"
        :src-images="product.imageLinks"
      />
      <div class="product__order">
        <div class="product__order-header">
          <span class="product__order-article">
            Артикул: {{ product.article }}
          </span>
          <span class="product__order-count">
            В наличии: <b>{{ product.count }} шт</b>
          </span>
        </div>
        <h2 class="product__order-title">
          {{ product.title }}
        </h2>
        <div class="product__order-rating-wrap">
          <span class="product__order-star" />
          <span class="product__order-star" />
          <span class="product__order-star" />
          <span class="product__order-star" />
          <span class="product__order-star" />
          <span class="product__order-rating">
            {{ product.rating[1] }}
          </span>
        </div>
        <AppImages
          v-if="width && width < 770"
          :src-images="product.imageLinks"
        />
        <h3 class="product__order-sub-title">
          Выберите размер
        </h3>
        <div class="product__order-sizes">
          <label
            v-for="size in product.sizes"
            :key="size"
            class="product__size-label"
          >
            <input
              v-model="currentSize"
              name="productSize"
              type="radio"
              :value="size"
              class="product__size-input"
              @click="checkSize"
            >
            <span class="product__size-number">
              {{ size }}
            </span>
          </label>
        </div>
        <div class="product__order-costs">
          <span class="product__order-current-cost">{{ Math.round(product.cost - (product.cost / 100 * product.discount)) }} ₽ </span>
          <span class="product__order-old-cost">{{ product.cost }} ₽</span>
        </div>
        <button class="product__order-btn-sibmit">
          Заказать
        </button>
        <ul class="product__list-conditions">
          <li class="product__list-item">
            Бесплатная доставка до двери
          </li>
          <li class="product__list-item">
            Оплата заказа при получении
          </li>
          <li class="product__list-item">
            Обмен в течении двух недель
          </li>
        </ul>
      </div>
      <div class="product__description">
        <h3 class="product__subtitle">
          Описание
        </h3>
        <p class="product__text">
          Кроссовки Nike Blazer Mid &rsquo;77 Vintage Suede с&nbsp;винтажной подошвой возрождают стиль баскетбольных моделей Nike прошлого, создавая впечатление, что они хранились в&nbsp;шкафу долгие годы.
        </p>
      </div>
      <div class="product__specifications">
        <h3 class="product__subtitle">
          Характеристики
        </h3>
        <span class="product__text">
          Пол: {{ product.gender === 'male'? 'Мужской' : 'Женский' }}
        </span>
        <span class="product__text">
          Цвета: Разноцветный
        </span>
        <span class="product__text">
          Состав: Кожа, текстиль, резина
        </span>
        <span class="product__text">
          Страна: Вьетнам
        </span>
      </div>
      <button class="product__btn-close" @click="openProduct" />
    </div>
  </section>
</template>

<script>
import AppImages from './images.vue'
export default {
  components: {
    AppImages
  },
  data () {
    return {
      currentSize: null
    }
  },
  computed: {
    product () {
      const id = this.$store.getters['data/currentProduct']
      return this.$store.getters['data/products'][id]
    },
    color () {
      if (this.product.colors === 'red') {
        return 'Красный'
      } else if (this.product.colors === 'multicolored') {
        return 'Разноцветный'
      } else if (this.product.colors === 'white') {
        return 'Белый'
      } else if (this.product.colors === 'black') {
        return 'Черный'
      } else {
        return this.product.colors
      }
    },
    width () {
      try {
        return document.documentElement.clientWidth
      } catch {
        return false
      }
    }
  },
  mounted () {
    this.fillStar()
  },
  methods: {
    openProduct () {
      this.$store.commit('data/productShow')
      document.body.classList.toggle('stop-scroll')
    },
    fillStar () {
      const wrapper = document.querySelector('.product__order-rating-wrap')
      const stars = wrapper.children
      const rating = Math.floor(this.product.rating[1])
      for (let index = 0; index < rating; index++) {
        stars[index].classList.add('product__order-star_fill')
      }
    },
    checkSize (event) {
      document.querySelectorAll('.product__size-label_vote').forEach((item) => {
        item.classList.remove('product__size-label_vote')
      })
      event.target.parentNode.classList.add('product__size-label_vote')
    }
  }
}
</script>

<style lang="scss">
.product {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 50;
  display: flex;
  flex-wrap: wrap;
  width: 100vw;
  height: 100vh;
  // min-height: 100vh;
  padding: 40px 3vw;
  background: rgba(68, 75, 88, 0.7);
  overflow-y: auto;

  &__wrapper {
    position: relative;
    display: grid;
    grid-template-rows: repeat(2, auto);
    grid-template-columns: 50% 50%;
    gap: 20px;
    width: 100%;
    padding: 40px;
    background: #fff;
    border-radius: 4px;
    overflow-y: auto;
  }

  // &__order {
  // }

  &__order-header {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    flex-wrap: wrap;
    width: 100%;
    margin-bottom: 25px;
  }

  &__order-article {
    margin-right: 50px;
    margin-bottom: 15px;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #b2b5bb;
  }

  &__order-count {
    margin-bottom: 15px;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #b2b5bb;
  }

  &__order-title {
    margin-bottom: 20px;
    font-family: "Intro Book", sans-serif;
    font-size: 24px;
    line-height: 140%;
    color: #444b58;
  }

  &__order-rating-wrap {
    display: flex;
    width: 120px;
    height: 20px;
    margin-bottom: 20px;
  }

  &__order-rating {
    margin-right: 8px;
    font-family: "Intro Book", sans-serif;
    font-size: 14px;
    line-height: 20px;
    color: #444b58;
  }

  &__order-star {
    display: inline-block;
    width: 20px;
    height: 20px;
    background-image: url("/images/icons/star.svg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: contain;
    opacity: 0.5;

    &_fill {
      opacity: 1;
    }
  }

  &__order-sub-title {
    margin-bottom: 20px;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #444b58;
  }

  &__order-sizes {
    display: flex;
    width: 100%;
    height: 32px;
    margin-bottom: 40px;
  }

  &__size-label {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 70px;
    height: 32px;
    border: 1px solid #b2b5bb;
    border-radius: 4px;
    transition: background-color 0.3s;

    &:not(:last-child) {
      margin-right: 20px;
    }

    &:hover {
      background-color: #dbbba97a;
      transition: background-color 0.3s;
    }

    &_vote {
      background-color: #dbbba97a;
    }
  }

  &__size-input {
    position: absolute;
    left: 0;
    height: 0;
    z-index: -1;
    opacity: 0;
  }

  &__size-number {
    font-family: "Intro Book", sans-serif;
    font-size: 14px;
    line-height: 14px;
    color: #444b58;
  }

  &__order-costs {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin-bottom: 80px;
  }

  &__order-current-cost {
    margin-right: 30px;
    font-family: "Intro Bold", sans-serif;
    font-style: normal;
    font-weight: bold;
    font-size: 30px;
    line-height: 30px;
    color: #444b58;
  }

  &__order-old-cost {
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #b2b5bb;
  }

  &__order-btn-sibmit {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px 9vw;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #fff;
    background: #f14f4f;
    border-radius: 4px;
  }

  &__list-conditions {
    // display: flex;
    // flex-direction: column;
    // align-items: flex-start;
    // justify-content: space-between;
    padding: 20px 0;
  }

  &__list-item {
    position: relative;
    display: block;
    padding-left: 20px;
    margin-bottom: 10px;
    font-family: "Intro Book", sans-serif;
    font-size: 14px;
    line-height: 14px;
    color: #b2b5bb;

    &::before {
      position: absolute;
      top: 0;
      left: 0;
      display: block;
      width: 14px;
      height: 14px;
      background-image: url("/images/icons/checked.png");
      background-repeat: no-repeat;
      background-position: center;
      background-size: contain;
      content: "";
    }
  }

  &__description {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding-bottom: 40px;
  }

  &__subtitle {
    margin-bottom: 20px;
    font-family: "Intro Book", sans-serif;
    font-size: 24px;
    line-height: 24px;
    color: #444b58;
  }

  &__text {
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 180%;
    color: #444b58;
  }

  &__specifications {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding-bottom: 40px;
  }

  &__btn-close {
    position: absolute;
    top: 20px;
    right: 20px;
    display: block;
    width: 42px;
    height: 42px;
    background-color: rgba(246, 113, 113, 0.65);
    background-image: url("/images/icons/cross.png");
    background-repeat: no-repeat;
    background-position: center;
    background-size: 25px;
    border-radius: 100%;
    transform: rotate(45deg);
    transition: background-color 0.3s;

    &:hover {
      background-color: rgb(245, 79, 79);
      transition: background-color 0.3s;
    }
  }
}

b {
  color: #444b58;
}

@media screen and (max-width: 960px) {
  .product {
    &__wrapper {
      padding: 40px 3vw;
      padding-top: 70px;
    }
  }
}

@media screen and (max-width: 770px) {
  .product {
    &__wrapper {
      display: flex;
      flex-direction: column;
    }
  }
}
</style>
