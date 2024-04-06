<template>
  <div class="shadow-md sm:rounded-lg relative overflow-x-auto">
    <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
      <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
      <tr>
        <th class="px-6 py-3">S/N</th>
        <th class="px-6 py-3">Name of Task</th>
        <th class="px-6 py-3">Assigned To</th>
        <th class="px-6 py-3">Status Update</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="toDo in slicedToDos" :key="toDo.id" class="odd:bg-white odd:dark:bg-gray-900 even:bg-gray-50 even:dark:bg-gray-800 border-b dark:border-gray-700">
        <td class="px-6 py-4">{{ toDo.id }}</td>
        <td class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">{{ toDo.title }}</td>
        <td class="px-6 py-4">{{ toDo.userId }}</td>
        <td class="px-6 py-4">{{ toDo.completed? 'Yes' : 'No' }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Table',
  props: {
    slicedToDos: {
      type: [Function, Array],
      required: true
    }
  },
}
</script>

<style>

</style>