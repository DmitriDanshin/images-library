<template>

  <div @click="close" class="w-full h-full bg-gray-400 opacity-50 z-10 fixed top-0 "></div>
  <img class="fixed to-center z-20 shadow-lg rounded-md opacity-100 h-5/6 "
       @wheel.prevent="zoomImage" ref="image"
       @mousedown.prevent='dragImage($event)' @mousemove.prevent="moveImage"
       @click="saveCoords"
       :src="src"
       alt="">
</template>

<script>
export default {
  name: "ZoomedImage",

  emits: {
    'close': null,
  },

  props: {
    src: {
      type: String,
      required: true,
    },
  },

  isDown: false,
  offset: [0, 0],
  mousePosition: {},

  data() {
    return {
      scale: 1,

    }
  },

  methods: {

    close() {
      this.$emit('close');
    },

    moveImage(event) {

      if (this.isDown) {
        this.mousePosition = {

          x: event.clientX,
          y: event.clientY

        };
        this.$refs.image.style.left = (this.mousePosition.x + this.offset[0]) + 'px';
        this.$refs.image.style.top = (this.mousePosition.y + this.offset[1]) + 'px';
      }

    },

    saveCoords(event) {

      this.isDown = false;
      this.$refs.image.style.left = event.target.x;
      this.$refs.image.style.left = event.target.x;

    },

    dragImage(event) {

      this.isDown = true;
      this.offset = [
        this.$refs.image.offsetLeft - event.clientX,
        this.$refs.image.offsetTop - event.clientY
      ];

    },

    zoomImage(event) {

      this.scale += event.deltaY * -0.001;

      this.scale = Math.min(Math.max(.125, this.scale), 4);

      this.$refs.image.style.transform = `translate(-50%, -50%) scale(${this.scale})`;
    }

  }
}
</script>

<style scoped>
.to-center {
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

</style>