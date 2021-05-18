<template>
  <section id="quiz" class="quiz container">
    <div class="quiz__wrapper">
      <div class="quiz__header">
        <h2 class="quiz__title title-section">
          {{ stepTitle }}
        </h2>
        <p class="quiz__description">
          {{ stepDescription }}
        </p>
      </div>
      <div class="quiz__content">
        <AppShoes v-if="currentStep === 1" />
        <AppSizes v-if="currentStep === 2" />
        <AppNotes v-if="currentStep === 3" />
        <AppRequest v-if="currentStep === 4" />
      </div>
      <div v-if="currentStep <= maxStep" class="quiz__footer">
        <div class="quiz__steps">
          <span class="quiz__step-number">
            {{ currentStep }}
          </span>
          <span>
            из
          </span>
          <span class="quiz__step-number">
            3
          </span>
        </div>
        <button
          :disabled="!stepUnlock"
          class="quiz__btn-next"
          @click="nextStep"
        >
          Следующий шаг
        </button>
      </div>
    </div>
  </section>
</template>
<script>
import AppShoes from './type-shoes.vue'
import AppSizes from './sizes.vue'
import AppNotes from './note.vue'
import AppRequest from './request.vue'

export default {
  components: {
    AppShoes,
    AppSizes,
    AppNotes,
    AppRequest
  },
  data () {
    return {
      currentStep: 1,
      maxStep: 3
    }
  },
  computed: {
    stepTitle () {
      if (this.currentStep <= this.maxStep) {
        return 'Мы подберем идеальную пару для вас'
      } else {
        return 'Ваша подборка готова!'
      }
    },
    stepDescription () {
      if (this.currentStep <= this.maxStep) {
        return 'Ответьте на три вопроса и мы вышлем каталог с самыми подходящими для вас моделями'
      } else {
        return 'Оставьте свои контактные данные, чтобы бы мы могли отправить  подготовленный для вас каталог'
      }
    },
    shoes () {
      return this.$store.getters['data/shoes']
    },
    stepUnlock () {
      if (this.currentStep === 1 && this.shoes.type) {
        return true
      } else if (this.currentStep === 2 && this.shoes.size) {
        return true
      } else if (this.currentStep === 3 && this.shoes.note) {
        return true
      } else {
        return false
      }
    }
  },
  methods: {
    nextStep () {
      this.currentStep++
    }
  }
}
</script>
<style lang="scss">
.quiz {
  height: max-content;
  padding: 40px 20px;
  background-color: #fff4ee;
  border-radius: 4px;

  &__wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 100%;
    max-width: 980px;
    height: 100%;
    margin: 0 auto;
  }

  &__header {
    margin-bottom: 20px;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #808080;
    border-bottom: 1px solid #808080;
  }

  &__description {
    margin-bottom: 20px;
  }

  &__content {
    display: flex;
    width: 100%;
    height: 400px;
  }

  &__footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding-top: 20px;
    margin-top: 20px;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #444b58;
    border-top: 1px solid #808080;
  }

  // &__steps {
  // }

  // &__step-number {
  // }

  &__btn-next {
    width: 211px;
    height: 50px;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #444b58;
    border: 1px solid #444b58;
    box-sizing: border-box;
    border-radius: 4px;
    background-color: transparent;

    &:disabled {
      opacity: 0.5;
    }
  }
}

.title-step {
  margin-bottom: 20px;
  font-family: "Intro Book", sans-serif;
  font-size: 24px;
  line-height: 24px;
  color: #444b58;
}

@media screen and (max-width: 600px) {
  .quiz {
    &__title {
      font-size: 26px;
    }
  }
}

@media screen and (max-width: 360px) {
  .quiz {
    &__btn-next {
      width: max-content;
      height: 40px;
      padding: 0 15px;
      font-size: 14px;
    }
  }
}
</style>
