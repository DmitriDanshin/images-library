<template>
  <nav class="my-3">
    <div class="flex justify-between ">
      <div class="flex justify-between items-center mx-4 cursor-default ">
        <div class="mx-4">
          Images Library
        </div>

        <div class="mr-1">
          <button @click="openEditor"
                  class='w-auto bg-gray-500 hover:bg-blue-400 rounded-lg shadow-xl font-medium text-white px-4 py-2 outline-none focus:outline-none '>
            New Image
          </button>

        </div>

      </div>
      <div class="pr-2 border border-blue-400 w-1/3 rounded-md">
        <input class="px-3 w-full h-full outline-none rounded-md" type="text" placeholder="Tags, names">
      </div>
      <div class="flex justify-between items-center mx-4">

        <button class='w-auto text-black font-medium  px-4 mx-2 py-2 focus:outline-none '>
          Sign up
        </button>

        <button
            class='w-auto bg-gray-500 hover:bg-blue-400 rounded-lg shadow-xl font-medium text-white px-4 mx-2 py-2 focus:outline-none'>
          Log in
        </button>

      </div>
    </div>
    <hr class="mt-2">
  </nav>

</template>

<script>
export default {
  name: "ImagesMenu",

  emits: {
    'open-editor': null,

  },

  methods: {
    openEditor() {
      this.$emit('open-editor');
    },

  }
}
</script>

<style scoped>

</style>