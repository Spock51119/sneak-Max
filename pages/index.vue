<template>
  <div class="container-page">
    <AppFirstSection />
    <AppCatalog />
    <AppAbout />
    <Appquiz />
    <AppOurTeam />
    <AppAsk />
    <AppContacts />
    <AppOrder />
  </div>
</template>

<script>
import AppFirstSection from '~/components/first.vue'
import AppCatalog from '~/components/catalog/catalog.vue'
import AppAbout from '~/components/about.vue'
import Appquiz from '~/components/quiz/index.vue'
import AppOurTeam from '~/components/our-team/our-team.vue'
import AppAsk from '~/components/ask/ask.vue'
import AppContacts from '~/components/contacts/index.vue'
import AppOrder from '~/components/order/index.vue'
export default {
  components: {
    AppFirstSection,
    AppCatalog,
    AppAbout,
    Appquiz,
    AppOurTeam,
    AppAsk,
    AppContacts,
    AppOrder
  }
}
</script>

<style lang="scss">
//
</style>
