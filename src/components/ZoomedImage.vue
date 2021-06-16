<template >
  <div @click="close" class="w-full h-full bg-gray-400 opacity-50 z-10 fixed top-0 "></div>
  <img @click="close" class="fixed to-center z-20 shadow-lg rounded-md opacity-100 "
       :src="src"
       alt="">
</template>

<script>
export default {
  name: "ZoomedImage",

  props: {
    src: {
      type: String,
      required: true,
    },
  },

  emits: {
    'close': null,
  },

  methods: {
    close() {
      this.$emit('close');
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