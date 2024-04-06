<template>
  <div class="flex justify-between">
    <div class="mr-4 items-center flex-nowrap">
      <input type="radio" v-model="show" value="all" checked @change="filter">
      <label class="whitespace-nowrap ml-1 text-gray-500">Show All</label>
    </div>
    <div class="mr-4 items-center flex-nowrap">
      <input type="radio" v-model="show" value="Yes" @change="filter">
      <label class="whitespace-nowrap ml-1 text-gray-500">No</label>
    </div>
    <div class="mr-4 items-center flex-nowrap">
      <input type="radio" v-model="show" value="No" @change="filter">
      <label class="whitespace-nowrap ml-1 text-gray-500">Yes</label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FilterButtons',
  data() {
    return {
      show: ''
    }
  },
  methods: {
    filter() {
      this.$emit("filter", this.show);
    }
  }
}
</script>

<style lang="scss" scoped>

</style>