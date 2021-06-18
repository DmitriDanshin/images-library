<template>

  <zoomed-image v-if="isZoomed" @close="closeZoomedImage"
                :src="srcOfZoomedImage"/>
  <images-menu @open-editor="isOpenEditor = true" @close-editor="isOpenEditor = false"/>
  <images-grid v-if="!isOpenEditor" :images="images" @zoom="zoomImage" @delete-image="deleteImage"/>
  <images-editor v-if="isOpenEditor" @back="isOpenEditor = false" @save="saveImage"/>

</template>

<script>
import ImagesMenu from "./ImagesMenu";
import ImagesGrid from "./ImagesGrid";
import ImagesEditor from "./ImagesEditor";
import ZoomedImage from "./ZoomedImage";

export default {
  name: "ImagesWrapper",

  data() {
    return {
      isOpenEditor: false,
      isZoomed: false,
      srcOfZoomedImage: '',
      imageToAdd: {},
      images: [
        [],
        [],
        [],
        [],
        [],
      ]
    }
  },

  mounted() {

    if (localStorage.getItem('images')) {
      this.images = JSON.parse(localStorage.getItem('images'));
    }

  },

  methods: {

    saveImage(img) {
      this.addImageToArray(img);
    },

    deleteImage(image) {

      this.images = this.images.map(col => col.filter(i => i !== image));
      this.saveToLocalStorage(this.images);

    },

    zoomImage(image) {
      this.srcOfZoomedImage = image.src;
      this.isZoomed = true;
    },

    closeZoomedImage() {
      this.isZoomed = false;
    },

    saveToLocalStorage(images) {
      localStorage.setItem('images', JSON.stringify(images));
    },

    addImageToArray(img) {

      const lengthsOfColumns = this.images.map(col => col.length);

      // find index of the smallest column
      const indexCol = lengthsOfColumns.indexOf(Math.min(...lengthsOfColumns));

      this.images[indexCol] = [...this.images[indexCol], img];

      this.saveToLocalStorage(this.images);

    },
  },
  components: {ZoomedImage, ImagesEditor, ImagesGrid, ImagesMenu}
}
</script>

<style scoped>

</style>