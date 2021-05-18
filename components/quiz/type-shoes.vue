<template>
  <div class="type-shoes">
    <h3 class="title-step type-shoes__title">
      Какой тип кроссовок рассматриваете?
    </h3>
    <ul class="type-shoes__list">
      <li
        v-for="item in types"
        :key="item"
        class="type-shoes__item"
      >
        <picture>
          <source srcset="/images/shoes.webp" type="image/webp">
          <source srcset="/images/shoes.jpg" type="image/jpg">
          <img src="/images/shoes.jpg" alt="Кеды" loading="lazy" class="type-shoes__illustration">
        </picture>
        <!-- <img src="/images/shoes.jpg" alt="Кеды" class="type-shoes__illustration"> -->
        <AppCheckBox
          name="shoes"
          :value="item"
          input-type="radio"
          :text="item"
          :current="shoes"
          @changeCheck="nextValue"
        />
      </li>
    </ul>
  </div>
</template>
<script>
import AppCheckBox from '~/components/common/checkBox.vue'
export default {
  components: {
    AppCheckBox
  },
  data () {
    return {
      types: ['Кеды', 'Беговые', 'Бутсы', 'Баскетбольные', 'Тенисные', 'Для ходьбы'],
      shoes: null
    }
  },
  methods: {
    nextValue (val) {
      this.shoes = val
      this.$store.commit('data/setShoes', [val, 'type'])
    }
  }
}
</script>
<style lang="scss">
.type-shoes {
  display: flex;
  width: 100%;
  flex-direction: column;

  // &__title {
  // }

  &__list {
    display: grid;
    grid-template-rows: repeat(2, 1fr);
    grid-template-columns: repeat(3, 280px);
    gap: 20px;
    width: 100%;
    justify-content: space-between;
  }

  &__item {
    display: flex;
    flex-direction: column;
  }

  &__illustration {
    width: 100%;
    max-width: 280px;
    height: auto;
    margin-bottom: 10px;
    border-radius: 4px;
  }
}

@media screen and (max-width: 1000px) {
  .type-shoes {
    &__list {
      grid-template-columns: repeat(3, 1fr);
    }

    &__illustration {
      max-width: initial;
    }
  }
}

@media screen and (max-width: 600px) {
  .type-shoes {
    &__list {
      grid-template-rows: repeat(3, 1fr);
      grid-template-columns: repeat(2, 1fr);
      height: 100%;
    }

    &__item {
      position: relative;
      display: flex;
      flex-direction: row;
      align-items: flex-end;

      &::before {
        position: absolute;
        bottom: 0;
        left: 0;
        z-index: 1;
        display: block;
        width: 100%;
        height: 30px;
        background-color: #fff;
        content: "";
      }
    }

    &__illustration {
      position: absolute;
      top: 0;
      left: 0;
      z-index: 0;
    }
  }
}

@media screen and (max-width: 400px) {
  .type-shoes {
    &__list {
      display: flex;
      flex-direction: column;
      // align-items: center;
      justify-content: space-between;
      padding: 20px 0;
    }

    &__item {
      position: relative;
      display: flex;
      flex-direction: row;
      align-items: flex-end;

      &::before {
        display: none;
      }
    }

    &__illustration {
      display: none;
    }
  }
}
</style>
