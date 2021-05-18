<template>
  <section class="order">
    <div class="order__wrapper container">
      <AppOrderCall />
      <AppInstagram />
    </div>
  </section>
</template>

<script>
import AppInstagram from './instagram.vue'
import AppOrderCall from './order-call.vue'
export default {
  components: {
    AppOrderCall,
    AppInstagram
  }
}
</script>

<style lang="scss">
.order {
  display: block;
  width: 100%;
  padding: 60px 0;

  &__wrapper {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
  }
}

@media screen and (max-width: 880px) {
  .order {
    &__wrapper {
      align-items: center;
      flex-direction: column;
    }
  }
}
</style>
