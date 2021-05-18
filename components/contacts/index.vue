<template>
  <section id="contacts" class="contacts">
    <div class="contacts__wrapper container">
      <AppText />
      <AppMap />
    </div>
  </section>
</template>

<script>
import AppText from './text.vue'
import AppMap from './map.vue'
export default {
  components: {
    AppText,
    AppMap
  }
}
</script>

<style lang="scss">
.contacts {
  display: block;
  width: 100%;
  padding: 60px 0;
  background-color: #f3f6f6;

  &__wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
}

@media screen and (max-width: 800px) {
  .contacts {
    &__wrapper {
      flex-direction: column;
    }
  }
}
</style>
