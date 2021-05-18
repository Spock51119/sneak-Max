<template>
  <form class="order-call">
    <h3 class="order-call__title">
      Есть вопросы?
    </h3>
    <p class="order-call__description">
      Заполните форму и наш менеджер свяжется с вами
    </p>
    <input type="text" class="order-call__input" placeholder="Ваше имя">
    <input type="text" class="order-call__input" placeholder="Номер телефона">
    <button class="order-call__btn-submit">
      Отправить
    </button>
  </form>
</template>

<script>
export default {
}
</script>

<style lang="scss">
.order-call {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 380px;
  padding: 40px 20px;
  margin-right: 20px;
  text-align: center;
  color: #fff;
  background-color: #484283;
  border-radius: 4px;

  &__title {
    margin-bottom: 20px;
    font-family: "Intro Bold", sans-serif;
    font-weight: bold;
    font-size: 30px;
    line-height: 30px;
  }

  &__description {
    max-width: 260px;
    margin-bottom: 40px;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 16px;
  }

  &__input {
    display: flex;
    align-items: center;
    width: 100%;
    height: 60px;
    padding: 0 20px;
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
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 60px;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #fff;
    background: #f14f4f;
    border-radius: 4px;
  }
}

@media screen and (max-width: 880px) {
  .order-call {
    margin-bottom: 20px;
    margin-right: 0;
  }
}
</style>
