<template>
  <section>

    <div class="grid grid-cols-5 gap-4 mx-4 ">

      <div v-for="imagesColumn in imagesColumns" class="h-full" :key="imagesColumn">
        <image-card v-for="image in imagesColumn" :image="image" :key="image" @zoom="zoom(image)"
                    @contextmenu.prevent="deleteImage(image)"/>
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
    'zoom': null,
    'delete-image': null,
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

    deleteImage(image) {
      this.$emit('delete-image', image);
    }

  },

}
</script>

<style scoped>
img {
  object-fit: cover;
}
</style>
