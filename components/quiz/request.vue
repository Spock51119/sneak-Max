<template>
  <div class="request">
    <form class="request__form">
      <h3 class="request__title">
        Получить предложение
      </h3>
      <p class="request__description">
        Получите подборку подходящих для вас моделей на почту
      </p>
      <input type="text" class="request__input" placeholder="Ваше имя">
      <input type="email" class="request__input" placeholder="E-mail">
      <button class="request__btn-submit">
        Получить
      </button>
    </form>
    <AppMobile v-if="width > 500" />
  </div>
</template>
<script>
import AppMobile from './mobile.vue'
export default {
  components: {
    AppMobile
  },
  computed: {
    width () {
      return document.documentElement.clientWidth
    }
  }
}
</script>
<style lang="scss">
.request {
  display: flex;
  // flex-direction: column;
  width: 100%;

  &__form {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 655px;
    padding: 40px;
    background: #dbbba9;
    border-radius: 4px;
  }

  &__title {
    margin-bottom: 10px;
    font-family: "Intro Bold", sans-serif;
    font-weight: bold;
    font-size: 36px;
    line-height: 140%;
    color: #fff;
  }

  &__description {
    margin-bottom: 25px;
    font-family: "Intro Book", sans-serif;
    font-size: 18px;
    line-height: 140%;
    color: #fff;
  }

  &__input {
    width: 100%;
    max-width: 500px;
    height: 60px;
    padding: 20px;
    margin-bottom: 10px;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 140%;
    color: #b2b5bb;
    border-radius: 4px;

    &:focus {
      color: #444b58;
    }
  }

  &__btn-submit {
    display: flex;
    flex-shrink: 0;
    align-items: center;
    justify-content: center;
    width: 220px;
    height: 60px;
    margin-top: 10px;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #fff;
    background: #f14f4f;
    border-radius: 4px;
  }
}

@media screen and (max-width: 1000px) {
  .request {
    text-shadow: 2px 2px 2px rgba(0, 0, 0, 0.6);

    &__title {
      font-size: 28px;
    }

    &__description {
      margin-bottom: 20px;
      font-size: 16px;
    }

    &__input {
      height: 50px;
      padding: 15px;
    }

    &__btn-submit {
      width: max-content;
      height: 50px;
      padding: 0 20px;
    }
  }
}

@media screen and (max-width: 620px) {
  .request {
    &__form {
      height: 100%;
      padding: 25px;
    }

    &__title {
      font-size: 26px;
    }

    &__input {
      height: 40px;
    }

    &__btn-submit {
      width: max-content;
      height: 40px;
    }
  }
}
</style>
