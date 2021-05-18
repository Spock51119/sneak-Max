<template>
  <section id="catalog" class="catalog">
    <div class="catalog__wrapper container">
      <AppProduct v-if="openProduct" />
      <h2 class="title-section">
        Каталог
      </h2>
      <button :class="['catalog__toggle-filters', { 'catalog__toggle-filters_open': openFilter }]" @click="openFilter = !openFilter" />
      <AppFilter
        :open-filter="openFilter"
        @commitFilters="filters"
        @resetFilter="addProducts"
      />
      <div class="catalog__cards-items">
        <AppCard
          v-for="product in productsList.slice(0, countCard)"
          :id="product.id"
          :key="product.article"
          :title="product.title"
          :cost="product.cost"
        />
        <button
          class="catalog__btn-show-more"
          @click="showMore"
        >
          Показать еще
        </button>
      </div>
    </div>
  </section>
</template>
<script>
import AppFilter from './filters.vue'
import AppCard from './card.vue'
import AppProduct from '~/components/product/index.vue'

const widthBreackPoint = 700
export default {
  components: {
    AppFilter,
    AppCard,
    AppProduct
  },
  data () {
    return {
      productsList: [],
      openFilter: false,
      mounted: false,
      width: null, // document.documentElement.clientWidth,
      countCard: 9
    }
  },
  computed: {
    products () {
      return this.$store.getters['data/products']
    },
    openProduct () {
      return this.$store.getters['data/openProduct']
    }
  },
  watch: {
    width (val) {
      if (val < widthBreackPoint) {
        this.countCard = 6
      } else {
        this.countCard = 9
      }
    }
  },
  mounted () {
    this.mounted = true
    this.width = document.documentElement.clientWidth

    this.addProducts()
  },
  methods: {
    filters (firstValue, secondValue, gender, size) {
      this.addProducts()
      this.productsList = this.productsList.filter((item) => {
        return (item.cost >= firstValue && item.cost <= secondValue)
      })

      this.productsList = this.productsList.filter((item) => {
        return (item.gender === gender)
      })

      if (size !== null) {
        this.productsList = this.productsList.filter((item) => {
          return (item.sizes.includes(size))
        })
      }
    },
    addProducts () {
      this.productsList = []
      for (const key of Object.keys(this.products)) {
        this.productsList.push({
          id: key,
          ...this.products[key]
        })
      }
    },
    showMore () {
      if (this.width < widthBreackPoint && this.countCard + 2 > this.productsList.length) {
        this.countCard = this.productsList.length
      } else if (this.width < widthBreackPoint && this.countCard + 2 < this.productsList.length) {
        this.countCard += 2
      } else if (this.width > widthBreackPoint && this.countCard + 3 > this.productsList.length) {
        this.countCard = this.productsList.length
      } else if (this.width > widthBreackPoint && this.countCard + 3 < this.productsList.length) {
        this.countCard += 3
      } else {
        this.countCard = this.productsList.length
      }
    }
  }
}
</script>
<style lang="scss">
.catalog {
  position: relative;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  width: 100%;
  margin: 30px auto;

  &__wrapper {
    display: flex;
    flex-wrap: wrap;
    // align-items: center;
    justify-content: space-between;
  }

  &__toggle-filters {
    display: none;
  }

  &__cards-items {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    justify-content: space-between;
    width: 100%;
    max-width: 880px;
  }

  &__btn-show-more {
    display: flex;
    align-items: center;
    justify-content: center;
    grid-column: 1/4;
    width: 200px;
    height: 60px;
    margin: 0 auto;
    font-family: "Intro Regular", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #fff;
    background: #f14f4f;
    border-radius: 4px;
  }
}

@media screen and (max-width: 1280px) {
  .catalog {
    &__toggle-filters {
      position: absolute;
      top: 40px;
      left: 3vw;
      z-index: 16;
      display: block;
      width: 42px;
      height: 42px;
      border-radius: 100%;
      background-color: #fff;
      background-image: url("/images/icons/filter.svg");
      background-repeat: no-repeat;
      background-position: center;
      background-size: 25px;
      box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.2);
      transition: left 0.4s, top 0.4s, background-image 0.4s;

      &_open {
        background-image: url("/images/icons/cross.png");
        top: 60px;
        left: calc(238px + 2vw);
        transform: rotate(45deg);
        transition: left 0.4s, top 0.4s, background-image 0.4s;
      }
    }

    &__cards-items {
      max-width: initial;
    }
  }
}

@media screen and (max-width: 700px) {
  .catalog {
    &__cards-items {
      grid-template-columns: repeat(2, 1fr);
    }

    &__btn-show-more {
      grid-column: 1/3;
    }
  }
}
</style>
