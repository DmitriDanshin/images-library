<template>
  <images-menu/>
  <images-grid/>
</template>

<script>
import ImagesMenu from "./ImagesMenu";
import ImagesGrid from "./ImagesGrid";

export default {
  name: "ImagesWrapper",
  components: {ImagesGrid, ImagesMenu}
}
</script>

<style scoped>

</style>