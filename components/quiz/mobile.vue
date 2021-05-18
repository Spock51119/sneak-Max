<template>
  <div class="mobile">
    <span class="mobile__text mobile__text_type">
      {{ shoes.type }}
    </span>
    <span class="mobile__text mobile__text_size">
      {{ shoes.size }}
    </span>
    <span class="mobile__text mobile__text_note">
      {{ shoes.note }}
    </span>
  </div>
</template>
<script>
export default {
  computed: {
    shoes () {
      return this.$store.getters['data/shoes']
    }
  }
}
</script>
<style lang="scss">
.mobile {
  display: flex;
  flex-direction: column;
  flex-shrink: 0;
  width: 205px;
  height: 412px;
  padding: 45px 20px;
  margin-top: -6px;
  margin-left: -25px;
  background-image: url("/images/mobile.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
  overflow: hidden;

  &__text {
    margin-bottom: 15px;
    font-size: 16px;
    line-height: 180%;
    color: #fff;

    &_type {
      padding-left: 40px;
      background-image: url("/images/icons/shoes.png");
      background-repeat: no-repeat;
      background-position: left center;
      background-size: 30px;
    }

    &_size {
      padding-left: 40px;
      background-image: url("/images/icons/size.png");
      background-repeat: no-repeat;
      background-position: left center;
      background-size: 30px;
    }

    &_note {
      padding-top: 35px;
      font-size: 12px;
      line-height: 20px;
      max-height: 215px;
      overflow: hidden;
      background-image: url("/images/icons/note.png");
      background-repeat: no-repeat;
      background-position: top left;
      background-size: 30px;
    }
  }
}
</style>
