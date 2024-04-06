<template>
  <div>
    <form class="py-3 flex items-center">
      <label for="search-box" class="sr-only">Search:</label>
      <div class="relative w-full">
        <input id="search-box" type="text" placeholder="Search Here" v-model="filter" @input="search" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg
        focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white
        dark:focus:ring-blue-500 dark:focus:border-blue-500">
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filter: ''
    }
  },
  methods: {
    search() {
      this.$emit("search", this.filter);
    }
  }
}
</script>

<style>

</style>