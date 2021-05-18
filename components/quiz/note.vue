<template>
  <div class="note">
    <h3 class="title-step note__title">
      Уточните какие-либо моменты
    </h3>
    <textarea
      v-model="textNote"
      placeholder="Введите сообщение"
      class="note__input"
      @change="nextValue"
    />
  </div>
</template>
<script>
export default {
  data () {
    return {
      textNote: null
    }
  },
  methods: {
    nextValue () {
      this.$store.commit('data/setShoes', [this.textNote, 'note'])
    }
  }
}
</script>
<style lang="scss">
.note {
  width: 100%;
  // &__title {
  // }

  &__input {
    display: block;
    width: 100%;
    max-width: 100%;
    min-width: 290px;
    height: 85%;
    max-height: 85%;
    min-height: 300px;
    padding: 20px;
    font-family: "Intro Book", sans-serif;
    font-size: 16px;
    line-height: 16px;
    color: #dbbba9;
    background: #fff;
    border-radius: 4px;

    &:focus {
      color: #444b58;
    }
  }
}
</style>
