<template>

  <section class="flex justify-center mt-6">
    <div class="w-full max-w-lg">
      <div class="flex flex-wrap  mb-6 w-full">
        <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="src">
          src
        </label>
        <input v-model="url"
               class="appearance-none block w-full bg-gray-200 text-gray-700 border rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"
               id="src" type="text" placeholder="src">
      </div>

      <div class="flex flex-wrap -mx-3 mb-2">
        <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
          <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="views">
            Views
          </label>
          <input v-model="views"
                 class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                 id="views" type="text" placeholder="Views">
        </div>
        <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
          <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="likes">
            Views
          </label>
          <input v-model="likes"
                 class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                 id="likes" type="text" placeholder="Likes">
        </div>
        <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
          <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="comments">
            Comments
          </label>
          <input v-model="comments"
                 class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                 id="comments" type="text" placeholder="Comments">
        </div>
      </div>
      <button @click="back"
              class='w-auto bg-gray-500 hover:bg-blue-400 rounded-lg shadow-xl font-medium text-white px-4 py-2 outline-none focus:outline-none mr-3 '>
        Back
      </button>
      <button @click="save"
              class='w-auto bg-gray-500 hover:bg-blue-400 rounded-lg shadow-xl font-medium text-white px-4 py-2 outline-none focus:outline-none '>
        Save Image
      </button>
    </div>

  </section>

</template>

<script>
export default {
  name: "ImagesEditor",

  emits: {
    'save': null,
    'back': null,
  },

  data() {
    return {

      url: '',
      likes: 0,
      comments: 0,
      views: 0,

    }
  },

  methods: {

    back() {
      this.$emit('back');
    },

    save() {

      const image = {
        url: this.url,
        likes: this.likes,
        comments: this.comments,
        views: this.views,
      };

      this.$emit('save', image);
      this.$emit('back');
    }

  }
}
</script>

<style scoped>

</style>