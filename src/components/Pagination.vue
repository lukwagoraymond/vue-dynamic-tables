<template>
  <!-- Table Component -->
  <Table :slicedToDos="displayedToDos" />
  <!-- Pagination Buttons -->
  <div class="my-8 table border-collapse text-center bg-inherit mx-auto space-x-2 text-gray-900">
    <!-- Previous Button -->
    <button type="button" class="w-8 h-8 border border-gray-200 table-cell hover:border-blue-300 hover:bg-blue-100 rounded-full transition duration-100 ease-in-out
      focus:ring-2 focus:ring-blue-500 focus:outline-none focus:ring-opacity-50" v-if="currentPage >= 1" @click="currentPage--;"><<</button>
    <!-- Allows # number of Buttons -->
    <button type="button" class="w-8 h-8 border border-gray-200 table-cell hover:border-blue-300 hover:bg-blue-100 rounded-full transition duration-100 ease-in-out
      focus:ring-2 focus:ring-blue-500 focus:outline-none focus:ring-opacity-50" v-for="pageNumber in pageNumbers.slice(currentPage-1, currentPage+5)"
      @click="currentPage=pageNumber;">{{ pageNumber }}</button>
    <!-- Next Button -->
    <button type="button" class="w-8 h-8 border border-gray-200 table-cell hover:border-blue-300 hover:bg-blue-100 rounded-full transition duration-100 ease-in-out
      focus:ring-2 focus:ring-blue-500 focus:outline-none focus:ring-opacity-50" v-if="currentPage < pageNumbers.length" @click="currentPage++;">>></button>
  </div>
</template>

<script>
import Table from "./Table.vue";
export default {
  name: 'Pagination',
  components: {Table},
  data() {
    return {
      currentPage: 1,
    }
  },
  emits: ['updated-Data'],
  props: {
    pageNumbers: {
      type: Array,
      required: true
    },
    tasks: {
      type: [Array, Function],
      required: true
    },
    recordsPerPage: {
      type: Number,
      required: true,
      default: 10
    }
  },
  methods: {
    pagination: function(posts) {
      let page = this.currentPage;
      let recordsPerPage = this.recordsPerPage;
      let lastIndexOfData = (page * recordsPerPage);
      let firstIndexOfData = (lastIndexOfData - recordsPerPage);
      return posts.slice(firstIndexOfData, lastIndexOfData);
    }
  },
  computed: {
    displayedToDos: function() {
      return this.pagination(this.tasks);
    }
  },
}
</script>

<style>

</style>