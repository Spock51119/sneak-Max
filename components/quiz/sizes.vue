<template>
  <div class="sizes">
    <h3 class="title-step sizes__title">
      Какой размер вам подойдет?
    </h3>
    <ul class="sizes__list">
      <li class="sizes__item">
        <AppCheckBox
          id="size"
          value="менее 36"
          input-type="radio"
          text="менее 36"
          :current="size"
          @changeCheck="nextValue"
        />
      </li>
      <li class="sizes__item">
        <AppCheckBox
          id="size"
          value="36-38"
          input-type="radio"
          text="36-38"
          :current="size"
          @changeCheck="nextValue"
        />
      </li>
      <li class="sizes__item">
        <AppCheckBox
          id="size"
          value="39-41"
          input-type="radio"
          text="39-41"
          :current="size"
          @changeCheck="nextValue"
        />
      </li>
      <li class="sizes__item">
        <AppCheckBox
          id="size"
          value="42-44"
          input-type="radio"
          text="42-44"
          :current="size"
          @changeCheck="nextValue"
        />
      </li>
      <li class="sizes__item">
        <AppCheckBox
          id="size"
          value="45 и больше"
          input-type="radio"
          text="45 и больше"
          :current="size"
          @changeCheck="nextValue"
        />
      </li>
    </ul>
    <picture>
      <source srcset="/images/sizeBg.webp" type="image/webp">
      <source srcset="/images/sizeBg.jpg" type="image/jpg">
      <img src="/images/sizeBg.jpg" alt="Иллюстрация" loading="lazy" class="sizes__illustration">
    </picture>
    <!-- <img src="/images/sizeBg.jpg" alt="Иллюстрация" class="sizes__illustration"> -->
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
      size: null
    }
  },
  methods: {
    nextValue (val) {
      this.size = val
      this.$store.commit('data/setShoes', [val, 'size'])
    }
  }
}
</script>
<style lang="scss">
.sizes {
  width: 100%;
  overflow: hidden;

  &__title {
    margin-bottom: 40px;
  }

  &__list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    width: 100%;
  }

  &__item {
    display: flex;
    flex-shrink: 0;
    margin-bottom: 20px;

    &:not(:last-child) {
      margin-right: 15px;
    }
  }

  &__illustration {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 4px;
  }
}
</style>
