<template>
  <section class="first">
    <div class="first__wrapper container">
      <div class="first__content">
        <h1 class="first__title">
          Кроссовки известных брендов с доставкой по России и СНГ
        </h1>
        <p class="first__description">
          Мы продаем кроссовки брендов Nike, Adidas, Puma, Reebok, Converse и многие другие по низким ценам
        </p>
        <button class="first__btn">
          Перейти к покупкам
        </button>
      </div>
    </div>
  </section>
</template>
<script>
export default {

}
</script>
<style lang="scss">
.first {
  display: block;
  background-color: #484283;
  width: 100%;
  height: 528px;
  padding-top: 164px;

  &__wrapper {
    position: relative;
    z-index: 2;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    height: 100%;
    background-image: url("/images/firstBg.svg");
    background-repeat: no-repeat;
    background-position: 88px center;
    background-size: 83% auto;
  }

  &__content {
    position: relative;
    z-index: 2;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    max-width: 585px;
    height: 100%;
  }

  &__title {
    margin-bottom: 20px;
    font-family: "Intro Regular", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 36px;
    line-height: 140%;
    color: #fff;
  }

  &__description {
    margin-bottom: 40px;
    font-family: "Intro Book", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 140%;
    color: #fff;
  }

  &__btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 250px;
    height: 60px;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    background: #f14f4f;
    border-radius: 4px;
    color: #fff;
  }
}

@media screen and (max-width: 700px) {
  .first {
    &__wrapper {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      height: 100%;
      background-image: url("/images/firstBg.svg");
      background-repeat: no-repeat;
      background-position: bottom right;
      background-size: 83% auto;
    }

    &__title {
      font-size: 26px;
    }

    &__description {
      font-size: 14px;
      line-height: 180%;
      margin-bottom: 30px;
    }

    &__btn {
      width: 200px;
      height: 60px;
      font-size: 14px;
      line-height: 14px;
    }
  }
}
</style>
