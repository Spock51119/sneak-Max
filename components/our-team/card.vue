<template>
  <div class="team-card">
    <picture>
      <source :srcset="'/images/team/team' + id + '.webp'" type="image/webp">
      <source :srcset="'/images/team/team' + id + '.jpg'" type="image/jpg">
      <img
        :src="'/images/team/team' + id + '.jpg'"
        alt="Фотография члена нашей команды"
        class="team-card__photo"
        loading="lazy"
      >
    </picture>
    <!-- <img
      :src="'/images/team/team' + id + '.jpg'"
      alt="Фотография члена нашей команды"
      class="team-card__photo"
    > -->
    <span class="team-card__name">
      Максим Золотораев
    </span>
    <span class="team-card__post">
      Администратор
    </span>
  </div>
</template>
<script>
export default {
  props: ['id']

}
</script>
<style lang="scss">
.team-card {
  display: flex;
  flex-direction: column;
  color: #fff;

  &__photo {
    display: block;
    margin: 0;
    width: 100%;
    height: auto;
    object-fit: contain;
    border-radius: 4px;
  }

  &__name {
    margin: 20px 0;
    font-family: "Intro Bold", sans-serif;
    font-style: normal;
    font-weight: bold;
    font-size: 24px;
    line-height: 24px;
  }

  &__post {
    margin-bottom: 20px;
    font-family: "Intro Book", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 16px;
  }
}

@media screen and (max-width: 580px) {
  .team-card {
    &__name {
      margin: 15px 0;
      margin-bottom: 10px;
      font-size: 18px;
    }

    &__post {
      font-size: 14px;
    }
  }
}
</style>
