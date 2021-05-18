<template>
  <div>
    <AppHeader />
    <main>
      <Nuxt />
    </main>
    <AppFooter />
  </div>
</template>

<script>
import AppHeader from '~/components/header/index.vue'
import AppFooter from '~/components/footer/footer.vue'
export default {
  components: {
    AppHeader,
    AppFooter
  }
}
</script>

<style lang="scss">
//
</style>
