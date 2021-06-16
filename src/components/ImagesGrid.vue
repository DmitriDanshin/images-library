<template>
  <section>

    <div class="grid grid-cols-5 gap-4 mx-4 ">

      <div v-for="imagesColumn in imagesColumns" class="h-full" :key="imagesColumn">
        <image-card v-for="image in imagesColumn" :image="image" :key="image" @zoom="zoom(image)"/>
      </div>


    </div>
  </section>
</template>

<script>
import ImageCard from "./ImageCard";

export default {
  name: "ImagesGrid",
  components: {ImageCard},
  IMAGE_HEIGHT_LIMIT: 350,

  emits: {
    'zoom': null
  },

  props: {
    images: {
      type: Array,
      required: true,
    },
  },

  computed: {
    imagesColumns() {
      return this.images;
    }
  },

  methods: {

    zoom(image) {
      this.$emit('zoom', image);
    },

    normalizeHeightOfImage(img, imagesColumn, event) {

      if (event.target.height > this.$options.IMAGE_HEIGHT_LIMIT) {

        // const indexCol = this.images.indexOf(imagesColumn);
        // const indexImg = this.images[indexCol].indexOf(img);

        // event.target.style.height = `${this.$options.IMAGE_HEIGHT_LIMIT}px`;
        event.target.style.height = `auto`;


      }
    },
  },

}
</script>

<style scoped>
img {
  object-fit: cover;
}
</style>
