<template>
  <section id="team" class="our-team">
    <div class="our-team__wrapper container">
      <h2 class="title-section title-section_white">
        Наша команда
      </h2>
      <div class="our-team__items">
        <AppTeamCard
          v-for="number in 6"
          :id="number"
          :key="number"
        />
      </div>
    </div>
  </section>
</template>
<script>
import AppTeamCard from './card.vue'
export default {
  components: {
    AppTeamCard
  }
}
</script>
<style lang="scss">
.our-team {
  background-color: #484283;
  background-image: url("/images/team/teamBg.svg");
  background-repeat: no-repeat;
  background-position: right top;
  background-size: 28vw 28.6vw;
  padding: 60px 0;

  // &__wrapper {
  // }

  &__items {
    display: grid;
    grid-template-rows: repeat(2, 1fr);
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    margin-top: 40px;
  }
}

@media screen and (max-width: 580px) {
  .our-team {
    &__items {
      grid-template-rows: repeat(3, 1fr);
      grid-template-columns: repeat(2, 1fr);
    }
  }
}
</style>
