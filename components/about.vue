<template>
  <section id="about" class="about">
    <div class="about__wrapper container">
      <div class="about__text">
        <h2 class="title-section title-section_white">
          Пара слов о нас
        </h2>
        <p class="about__decription">
          Спорт держит нас в&nbsp;форме. Учит дисциплине. Объединяет нас. Через спорт мы&nbsp;можем менять жизни. В&nbsp;том числе с&nbsp;помощью воодушевляющих историй спортсменов. Чтобы помочь тебе подняться и&nbsp;двигаться вперед.
        </p>
        <span class="about__sign">
          SneakMax
        </span>
      </div>
      <picture>
        <source srcset="/images/about.webp" type="image/webp">
        <source srcset="/images/about.png" type="image/png">
        <img src="/images/about.png" alt="Иллюстрация" loading="lazy" class="about__illustration">
      </picture>
      <!-- <img src="/images/about.png" alt="Иллюстрация" class="about__illustration"> -->
    </div>
  </section>
</template>
<script>
export default {

}
</script>
<style lang="scss">
$bg: #484283;

.about {
  background-color: $bg;
  margin: 30px 0;
  background-image: url("/images/circles.svg");
  background-repeat: no-repeat;
  background-position: left top;
  background-size: 28vw auto;
  overflow: hidden;

  &__wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: max-content;
    // overflow: hidden;
  }

  &__text {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 50%;
    max-width: 445px;
    height: 100%;
    color: #fff;
  }

  &__decription {
    max-width: 380px;
    margin-bottom: 20px;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 140%;
    color: #fff;
  }

  &__sign {
    display: flex;
    align-items: center;
    margin-left: auto;
    font-family: "Intro Bold", sans-serif;
    font-size: 20px;
    line-height: 20px;
    color: #fff;

    &::before {
      display: block;
      width: 30px;
      height: 3px;
      margin-right: 20px;
      content: "";
      background-color: #fff;
    }
  }

  &__illustration {
    width: 100%;
    height: auto;
    object-fit: contain;
  }
}

@media screen and (max-width: 700px) {
  .about {
    position: relative;
    padding: 30px 0;

    &__text {
      position: relative;
      z-index: 2;
      width: 70%;
      max-width: initial;
      text-shadow: 4px 4px 2px rgba(0, 0, 0, 0.8);
    }

    &__decription {
      max-width: initial;
    }

    &__illustration {
      position: absolute;
      top: 0;
      right: -17%;
      z-index: 0;
      width: auto;
      height: 100%;
    }
  }
}

@media screen and (max-width: 500px) {
  .about {
    &__text {
      width: 100%;
    }

    &__decription {
      font-size: 14px;
    }

    &__illustration {
      position: absolute;
      top: 0;
      right: -30%;
      z-index: 0;
      width: auto;
      height: 100%;
    }
  }
}
</style>
