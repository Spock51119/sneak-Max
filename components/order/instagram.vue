<template>
  <div class="instagram">
    <picture>
      <source srcset="/images/instagram/image1.webp" type="image/webp">
      <source srcset="/images/instagram/image1.png" type="image/png">
      <img src="/images/instagram/image1.png" alt="Фотография из инстаграма" class="instagram__photo" loading="lazy">
    </picture>

    <picture>
      <source srcset="/images/instagram/image2.webp" type="image/webp">
      <source srcset="/images/instagram/image2.png" type="image/png">
      <img src="/images/instagram/image2.png" alt="Фотография из инстаграма" class="instagram__photo" loading="lazy">
    </picture>
    <picture>
      <source srcset="/images/instagram/image3.webp" type="image/webp">
      <source srcset="/images/instagram/image3.png" type="image/png">
      <img src="/images/instagram/image3.png" alt="Фотография из инстаграма" class="instagram__photo" loading="lazy">
    </picture>
    <picture class="instagram__photo instagram__photo_center">
      <source srcset="/images/instagram/image4.webp" type="image/webp">
      <source srcset="/images/instagram/image4.png" type="image/png">
      <img src="/images/instagram/image4.png" alt="Фотография из инстаграма" class="instagram__photo instagram__photo_center" loading="lazy">
    </picture>
    <picture>
      <source srcset="/images/instagram/image5.webp" type="image/webp">
      <source srcset="/images/instagram/image5.png" type="image/png">
      <img src="/images/instagram/image5.png" alt="Фотография из инстаграма" class="instagram__photo" loading="lazy">
    </picture>
    <!-- <img src="/images/instagram/image1.png" alt="Фотография из инстаграма" class="instagram__photo">
    <img src="/images/instagram/image2.png" alt="Фотография из инстаграма" class="instagram__photo">
    <img src="/images/instagram/image3.png" alt="Фотография из инстаграма" class="instagram__photo">
    <img src="/images/instagram/image4.png" alt="Фотография из инстаграма" class="instagram__photo instagram__photo_center">
    <img src="/images/instagram/image5.png" alt="Фотография из инстаграма" class="instagram__photo"> -->
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss">

.instagram {
  display: grid;
  grid-template-rows: repeat(2, 1fr);
  grid-template-columns: repeat(4, 1fr);
  row-gap: 15px;
  column-gap: 18px;
  padding-top: 75px;
  background-image: url("/images/instagram/instagram-logo.png");
  background-repeat: no-repeat;
  background-position: top center;

  &__photo {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 4px;

    &_center {
      grid-area: 1/2/3/4;
    }
  }
}

</style>
