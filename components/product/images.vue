<template>
  <div class="illustrations">
    <div class="illustrations__wrapper">
      <!-- <img :src="voteSrc" alt="Выбранное изображение" class="illustrations__vote"> -->
      <picture class="illustrations__vote">
        <source :srcset="voteSrc + 'webp'" type="image/webp">
        <source :srcset="voteSrc + 'jpg'" type="image/jpg">
        <img :src="voteSrc + 'jpg'" alt="Выбранное изображение" loading="lazy" class="illustrations__vote-img">
      </picture>
      <div class="illustrations__items">
        <picture
          v-for="(itemSrc, index) in srcImages"
          :key="index"
          class="illustrations__item"
          @click="changeImage(itemSrc)"
        >
          <source :srcset="itemSrc + 'webp'" type="image/webp">
          <source :srcset="itemSrc + 'jpg'" type="image/jpg">
          <img :src="itemSrc + 'jpg'" :alt=" 'Изображение ' + index + 1" loading="lazy" class="illustrations__item">
        </picture>
        <!-- <img
          v-for="(itemSrc, index) in srcImages"
          :key="index"
          :src="itemSrc"
          :alt=" 'Изображение ' + index + 1"
          class="illustrations__item"
          @click="changeImage(itemSrc)"
        > -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['src-images'],
  data () {
    return {
      voteSrc: this.srcImages[0]
    }
  },
  methods: {
    changeImage (itemSrc) {
      this.voteSrc = itemSrc
    }
  }
}
</script>

<style lang="scss">
.illustrations {
  display: flex;
  flex-shrink: 1;
  width: 100%;
  max-width: 520px;
  height: 100%;
  max-height: 557px;
  margin: 0 auto;

  &__wrapper {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    width: 100%;
    height: 100%;
  }

  &__vote {
    display: block;
    width: 100%;
    height: max-content;
    object-fit: contain;
    overflow: hidden;
  }

  &__vote-img {
    width: 100%;
  }

  &__items {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: max-content;
    max-width: 100%;
    overflow-x: auto;
    overflow-y: hidden;
    height: 15%;
    padding-top: 20px;
  }

  &__item {
    display: inline-block;
    width: 70px;
    height: 70px;
    cursor: pointer;

    &:not(:last-child) {
      margin-right: 20px;
    }
  }
}

@media screen and (max-width: 770px) {
  .illustrations {
    height: max-content;
    margin-bottom: 30px;
  }
}
</style>
