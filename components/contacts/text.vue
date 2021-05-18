<template>
  <div class="contacts-text">
    <h2 class="contacts-text__title title-section">
      Контакты
    </h2>
    <div class="contacts-text__wrap-sub-title">
      <h3 class="contacts-text__sub-title">
        Главный офис
      </h3>
      <div class="contacts-text__tooltip" @mouseover="tooltipFlag = !tooltipFlag" @mouseout="tooltipFlag = !tooltipFlag">
        ?
        <span v-if="tooltipFlag" class="contacts-text__tultip-text">
          Адрес и телефон для корреспонденции, инвесторов. Вопросы о доставке, качестве обслуживания и товара просьба задавать в отдел продаж
        </span>
      </div>
    </div>
    <a href="tel:78007898989" class="contacts-text__tel-number">+7 800 789 89 89</a>
    <span class="contacts-text__addres">г. Санкт-Петербург, Комсомольская, 43 к1</span>
    <h3 class="contacts-text__sub-title">
      отдел продаж
    </h3>
    <a href="tel:78007898989" class="contacts-text__tel-number">+7 800 789 89 89</a>
    <span class="contacts-text__addres">г. Санкт-Петербург, Комсомольская, 43 к1</span>
    <div class="contacts-text__social-links">
      <a href="#" class="contacts-text__social-link contacts-text__social-link_vk" aria-label="Ссылка на вконтакте" />
      <a href="#" class="contacts-text__social-link contacts-text__social-link_instagram" aria-label="Ссылка на инстаграм" />
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      tooltipFlag: false
    }
  }
}
</script>

<style lang="scss">
.contacts-text {
  display: flex;
  flex-direction: column;
  width: 40%;
  max-width: 420px;

  // &__title {
  // }

  &__wrap-sub-title {
    display: flex;
    align-items: center;
  }

  &__sub-title {
    padding: 20px 0;
    font-family: "Intro Book", sans-serif;
    font-size: 14px;
    line-height: 140%;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: #b2b5bb;
  }

  &__tooltip {
    position: relative;
    z-index: 5;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 20px;
    height: 20px;
    margin-left: 10px;
    font-family: "Intro Bold", sans-serif;
    font-weight: 700;
    color: #444b58;
    cursor: help;
    border-radius: 100%;
    box-shadow: 0 5px 14px 7px rgba(34, 60, 80, 0.2);
  }

  &__tultip-text {
    position: absolute;
    top: -100px;
    left: -30px;
    z-index: 4;
    // display: block;
    width: 446px;
    height: max-content;
    padding: 10px 20px;
    font-family: "Intro Book", sans-serif;
    font-weight: 400;
    font-size: 14px;
    line-height: 140%;
    color: #444b58;
    background-color: #fff;
    border-radius: 4px;
    box-shadow: 0 5px 18px 7px rgba(34, 60, 80, 0.2);
    opacity: 0;
    transition: opacity 0.4s;

    &::before {
      position: absolute;
      bottom: -10px;
      left: 25px;
      z-index: 3;
      display: block;
      width: 30px;
      height: 15px;
      background-image: url("/images/icons/Ellipse.png");
      background-repeat: no-repeat;
      background-position: center;
      background-size: contain;
      content: "";
    }
  }

  &__tooltip:hover &__tultip-text {
    opacity: 1;
    transition: opacity 0.4s;
  }

  &__tel-number {
    display: block;
    width: max-content;
    margin-bottom: 10px;
    font-family: "Intro Regular", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 30px;
    line-height: 140%;
    color: #444b58;
  }

  &__addres {
    margin-bottom: 20px;
    font-family: "Intro Book", sans-serif;
    font-size: 18px;
    line-height: 140%;
    color: #444b58;
  }

  &__social-links {
    display: flex;
    align-items: center;
    width: max-content;
    padding: 20px 0;
  }

  &__social-link {
    display: block;
    width: 44px;
    height: 44px;
    border-radius: 100%;
    background-color: #0e5a4c;
    background-repeat: no-repeat;
    background-position: center;
    background-size: contain;

    &:not(:last-child) {
      margin-right: 20px;
    }
  }

  &__social-link_vk {
    background-image: url("/images/icons/VK.svg");
  }

  &__social-link_instagram {
    background-image: url("/images/icons/Instagram.svg");
  }
}

@media screen and (max-width: 800px) {
  .contacts-text {
    width: 100%;
  }
}

@media screen and (max-width: 600px) {
  .contacts-text {
    &__tultip-text {
      top: -110px;
      left: -130px;
      width: 400px;

      &::before {
        left: 125px;
      }
    }
  }
}

@media screen and (max-width: 440px) {
  .contacts-text {
    &__tultip-text {
      top: -130px;
      left: -130px;
      width: 290px;

      &::before {
        left: 125px;
      }
    }
  }
}
</style>
