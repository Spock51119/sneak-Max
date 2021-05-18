<template>
  <div class="map">
    <iframe
      src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d8020.514395546929!2d30.132792028922132!3d59.83039531968783!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x46963beda42d23b7%3A0x8d20101d400e0748!2zMi3RjyDQmtC-0LzRgdC-0LzQvtC70YzRgdC60LDRjyDRg9C7LiwgNDMsINCh0LDQvdC60YIt0J_QtdGC0LXRgNCx0YPRgNCzLCAxOTgyNjQ!5e0!3m2!1sru!2sru!4v1620988977801!5m2!1sru!2sru"
      width="100%"
      height="100%"
      style="border: 0;"
      allowfullscreen=""
      loading="lazy"
    />
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss">
.map {
  display: block;
  width: 60%;
  max-width: 680px;
}

@media screen and (max-width: 800px) {
  .map {
    width: 100%;
    max-width: initial;
    height: 250px;
    margin-top: 30px;
  }
}
</style>
