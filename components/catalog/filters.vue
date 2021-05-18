<template>
  <div :class="['filters', { 'filters_open': openFilter }]">
    <h2 class="filters__title">
      Подбор<br>по параметрам
    </h2>
    <div class="filters__cost">
      <h3 class="filters__type">
        Цена, руб
      </h3>
      <div class="filters__min-max">
        <input
          v-model.number="firstValue"
          type="number"
          :min="0"
          :max="secondValue"
          class="filters__input filters__input_min"
        >
        <input
          v-model.number="secondValue"
          type="number"
          :min="firstValue + 500"
          :max="maxValueProducts"
          class="filters__input filters__input_max"
        >
      </div>
      <div class="filters__range-wrap">
        <input
          v-model.number="firstValue"
          type="range"
          :min="0"
          :max="maxValueProducts"
          step="10"
          class="filters__range"
        >
        <input
          v-model.number="secondValue"
          type="range"
          :min="0"
          :max="maxValueProducts"
          step="11"
          class="filters__range"
        >
      </div>
      <h3 class="filters__type">
        Пол
      </h3>
      <div class="filters__gender-wrap">
        <AppCheckBox
          name="gender"
          value="male"
          input-type="radio"
          text="Мужской"
          :current="gender"
          @changeCheck="nextValue"
        />
        <AppCheckBox
          name="gender"
          value="female"
          input-type="radio"
          text="Женский"
          :current="gender"
          @changeCheck="nextValue"
        />
      </div>
      <h3 class="filters__type">
        Размер
      </h3>
      <div class="filters__sizes-wrap">
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="35"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            35
          </span>
        </label>
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="36"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            36
          </span>
        </label>
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="37"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            37
          </span>
        </label>
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="38"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            38
          </span>
        </label>
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="39"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            39
          </span>
        </label>
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="40"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            40
          </span>
        </label>
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="41"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            41
          </span>
        </label>
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="42"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            42
          </span>
        </label>
        <label class="filters__size-label">
          <input
            v-model="size"
            name="size"
            type="radio"
            value="43"
            class="filters__size"
            @click="checkSize"
          >
          <span class="filters__size-number">
            43
          </span>
        </label>
      </div>
      <button class="filters__btn-submit" @click="dispatchFilters">
        Применить
      </button>
      <button class="filters__btn-reset" @click="resetValue">
        сбросить
      </button>
    </div>
  </div>
</template>
<script>
import AppCheckBox from '~/components/common/checkBox.vue'
export default {
  components: {
    AppCheckBox
  },
  props: ['open-filter'],
  data () {
    return {
      firstValue: 500,
      secondValue: 14300,
      gender: 'female',
      size: null
    }
  },
  computed: {
    products () {
      return this.$store.getters['data/products']
    },
    maxValueProducts () {
      let maxCost = 0
      for (const key of Object.keys(this.products)) {
        if (maxCost < Number(this.products[key].cost)) {
          maxCost = Number(this.products[key].cost)
        }
      }
      return maxCost
    }
  },
  watch: {
    firstValue (val) {
      if (this.firstValue > this.secondValue) {
        const tmp = this.firstValue
        this.firstValue = this.secondValue
        this.secondValue = tmp
      }
    },
    secondValue (val) {
      if (this.firstValue > this.secondValue) {
        const tmp = this.firstValue
        this.firstValue = this.secondValue
        this.secondValue = tmp
      }
    }
  },
  methods: {
    nextValue (val) {
      this.gender = val
    },
    checkSize (event) {
      document.querySelectorAll('.filters__size-label_vote').forEach((item) => {
        item.classList.remove('filters__size-label_vote')
      })
      event.target.parentNode.classList.add('filters__size-label_vote')
    },
    resetValue () {
      this.firstValue = 500
      this.secondValue = 14300
      this.gender = 'female'
      this.size = null

      document.querySelectorAll('.filters__size-label_vote').forEach((item) => {
        item.classList.remove('filters__size-label_vote')
      })

      this.$emit('resetFilter')
    },
    dispatchFilters () {
      this.$emit('commitFilters', this.firstValue, this.secondValue, this.gender, this.size)
    }
  }
}
</script>
<style lang="scss">
.filters {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 280px;
  height: max-content;
  padding: 20px;
  // margin-right: 30px;
  background: #fff4ee;
  border: 1px solid #fff4ee;
  box-sizing: border-box;
  border-radius: 4px;

  // &__cost {
  // }

  &__title {
    font-family: "Intro Book", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 24px;
    line-height: 24px;
    display: flex;
    align-items: center;
    color: #444b58;
    // border: 1px solid #FFF4EE;
  }

  &__type {
    margin-top: 20px;
    margin-bottom: 10px;
    font-family: "Intro Book", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 16px;
    color: #444b58;
  }

  &__min-max {
    display: flex;
    width: 240px;
    height: 50px;
    border: 1px solid #b2b5bb;
    box-sizing: border-box;
    border-radius: 4px;
  }

  &__input {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 50%;
    -moz-appearance: none;
    -webkit-appearance: none;
    appearance: none;
    text-align: center;
  }

  // &__input_min {
  // }

  // &__input_max {
  // }

  &__range-wrap {
    position: relative;
    display: flex;
    align-items: center;
    width: 100%;
    height: 1px;
    background-color: #ccc;
  }

  &__range {
    position: absolute;
    z-index: 0;
    -webkit-appearance: none;
    appearance: none;
    width: 240px;
    height: 2px;
    background-color: #000;
  }

  &__gender-wrap {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
  }

  // &__label {}

  &__gender {
    position: absolute;
    z-index: -1;
    opacity: 0;
    margin: 10px 0 0 7px;
  }

  &__label-text {
    position: relative;
    padding: 0 0 0 35px;
    font-family: "Intro Book", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 16px;
    color: #444b58;
    cursor: pointer;

    &::before {
      content: '';
      position: absolute;
      top: -2px;
      left: 0;
      width: 24px;
      height: 24px;
      border: 1px solid #cdd1da;
      border-radius: 3px;
      background: #fff;
    }

    &::after {
      content: '';
      position: absolute;
      top: -2px;
      left: 0;
      width: 24px;
      height: 24px;
      border-radius: 3px;
      background: transparent;
      box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.5);
      background-image: url("/images/icons/checked.svg");
      background-repeat: no-repeat;
      background-position: center;
      opacity: 0;
      transition: 0.2s;
    }
  }

  &__gender:checked + &__label-text::after {
    opacity: 1;
  }

  &__gender:focus + &__label-text::before {
    box-shadow: 0 0 0 3px rgba(186, 214, 241, 0.363);
  }

  &__sizes-wrap {
    display: grid;
    grid-template-rows: repeat(3, 1fr);
    grid-template-columns: repeat(3, 1fr);
    justify-content: center;
    gap: 0;
    margin-bottom: 20px;
    border-radius: 5px;
    border: 1px solid #b9826780;
  }

  &__size-label {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 57px;
    border: 0.5px solid #b9826775;
    background-color: #fff;
    cursor: pointer;

    &_vote {
      background-color: #b2b5bb;
    }
  }

  &__size {
    position: absolute;
    opacity: 1;
    z-index: -1;
  }

  &__size-number {
    font-family: "Intro Book", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 16px;
    display: flex;
    align-items: center;
    text-align: center;
    color: #444b58;
  }

  &__btn-submit {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 60px;
    font-family: "Intro Regular", sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 16px;
    color: #fff;
    border-radius: 4px;
    background: #444b58;
  }

  &__btn-reset {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 32px;
    margin: 15px auto;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #444b58;
    background-color: transparent;
  }
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

input[type='number'] {
  -moz-appearance: textfield;
}

@media screen and (max-width: 1280px) {
  .filters {
    position: absolute;
    left: calc(-100% + -3vw);
    top: 50px;
    z-index: 15;
    transition: left 0.4s;

    &_open {
      position: absolute;
      left: 3vw;
      top: 50px;
      transition: left 0.4s;
    }
  }
}

input[type='range']::-moz-range-thumb {
  z-index: 10;
  display: block;
  -webkit-appearance: none;
  border: 1px solid #000;
  height: 20px;
  width: 3px;
  border-radius: 2px;
  background: #000;
  cursor: ew-resize;
}

input[type='range']::-webkit-slider-thumb {
  z-index: 10;
  display: block;
  -webkit-appearance: none;
  border: 1px solid #000;
  height: 20px;
  width: 3px;
  border-radius: 2px;
  background: #000;
  cursor: ew-resize;
}
</style>
