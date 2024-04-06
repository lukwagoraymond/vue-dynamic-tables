<script>

import Pagination from "./Pagination.vue";
import SearchForm from "./SearchForm.vue";
import FilterButtons from "./FilterButtons.vue";

export default {
  name: 'ToDo',
  components: {Pagination, SearchForm, FilterButtons},
  async created() {
    this.toDos = await this.loadToDosFromAPI();
    this.staff = await this.loadUsersFromAPI();
    this.filteredTo = this.filteredToDos;
  },
  mounted() {


  },

  data() {
    return {
      toDos: [],
      staff: [],
      filteredTo: [],
      recordsPerPage: 10,
      pageNumbers: [],
      searchFilter: undefined,
      buttonFilter: undefined

    }
  },

  methods: {
    async loadToDosFromAPI() {
      const response = await fetch('https://jsonplaceholder.typicode.com/todos');
      return await response.json();
    },
    loadUsersFromAPI: async function() {
      const response = await fetch('https://jsonplaceholder.typicode.com/users');
      return await response.json();
    },
    setPages: function() {
      let numberOfPages = Math.ceil(this.filteredTo.length / this.recordsPerPage);
      for(let i = 1; i <= numberOfPages; i++) {
        this.pageNumbers.push(i);
      }
    },
    handleSearch: function(search) {
      this.searchFilter = search;
    },
    handleFilter: function(filter) {
      this.buttonFilter = filter;
    }
  },
  computed: {
    filteredToDos: function() {
      let items = this.toDos;
      switch(this.buttonFilter) {
        case 'No':
          items = items.filter(item => item.completed === false)
          break;
        case 'Yes':
          items = items.filter(item => item.completed === true)
          break;
      }
      if(this.searchFilter !== undefined) {
        items = items.filter(toDo => toDo.title.includes(this.searchFilter));
      }
      return items;
    }
  },
  watch: {
    filteredTo () {
      this.setPages();
    },

  }
}
</script>

<template>
  <div class="bg-inherit relative m-10">
    <!-- Filter Header Components -->
    <div class="flex items-center justify-between">
      <!-- Search Component -->
      <SearchForm @search="handleSearch" />
      <!-- Filter Radio Button Component -->
      <FilterButtons @filter="handleFilter" />
    </div>
    <!-- Pagination Component -->
    <div>
      <Pagination :pageNumbers="pageNumbers" :tasks="filteredToDos" :recordsPerPage="recordsPerPage" />
    </div>
  </div>

</template>

<style>

</style>