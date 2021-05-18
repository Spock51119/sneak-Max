<template>
  <div class="item-ask">
    <h3 class="item-ask__title">
      Вопрос {{ id }}
    </h3>
    <p :class="['item-ask__answer', {'item-ask__answer_open': openFlag}]">
      А это ответ {{ id }}: в комплексе функционируют 6 детских садов с площадками, воспитателями и всякими другими людьми
    </p>
    <button
      :class="['item-ask__btn', {'item-ask__btn_open': openFlag}]"
      :aria-label="openFlag? 'Закрыть ответ' : 'Открыть ответ'"
      @click="openFlag = !openFlag"
    />
  </div>
</template>
<script>
export default {
  props: ['id'],
  data () {
    return {
      openFlag: false
    }
  }
  // computed: {

  // }
}
</script>
<style lang="scss">
.item-ask {
  position: relative;

  &:not(:last-child) {
    border-bottom: 1px solid #242424;
  }

  &__title {
    padding: 30px 0;
    font-family: "Intro Regular", sans-serif;
    font-size: 20px;
    line-height: 20px;
    color: #242424;
  }

  &__answer {
    display: block;
    width: 100%;
    height: auto;
    max-height: 0;
    padding: 0;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 140%;
    color: rgba(36, 36, 36, 0.5);
    overflow: hidden;
    transition: max-height 0.5s, padding 0.5s;

    &_open {
      max-height: 110px;
      padding: 0 0 20px 0;
      transition: max-height 0.5s, padding 0.5s;
    }
  }

  &__btn {
    position: absolute;
    top: 24px;
    right: 0;
    display: block;
    width: 32px;
    height: 32px;
    background-color: transparent;

    &::before {
      display: block;
      width: 100%;
      height: 100%;
      content: "";
      background-image: url("/images/icons/cross.png");
      background-repeat: no-repeat;
      background-position: center;
      background-size: 25px;
      transition: transform 0.4s;
    }

    &_open::before {
      transform: rotate(45deg);
      transition: transform 0.4s;
    }
  }
}
</style>
