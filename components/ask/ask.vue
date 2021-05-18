<template>
  <section id="ask" class="ask">
    <div class="ask__wrapper container">
      <h2 class="ask__title title-section">
        Часто задаваемые вопросы
      </h2>
      <div class="ask__items">
        <AppItemAsk
          v-for="i in 2"
          :id="i"
          :key="i"
        />
      </div>
    </div>
  </section>
</template>
<script>
import AppItemAsk from './item-ask.vue'
export default {
  components: {
    AppItemAsk
  }
}
</script>
<style lang="scss">
.ask {
  padding: 60px 0;
  // &__wrapper {
  // }

  // &__title {
  // }

  &__items {
    display: flex;
    flex-direction: column;
    width: 85%;
    margin-top: 40px;
    margin-left: auto;
    border-top: 1px solid #242424;
    border-bottom: 1px solid #242424;
  }
}

@media screen and (max-width: 500px) {
  .ask {
    &__title {
      font-size: 26px;
    }

    &__items {
      width: 100%;
    }
  }
}
</style>
