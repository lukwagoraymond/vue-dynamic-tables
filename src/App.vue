<script>
import ToDo from "./components/ToDo.vue";
import AuthorProfile from "./components/AuthorProfile.vue";
export default {
  name: 'App',
  components:{AuthorProfile, ToDo}
}
</script>

<template>
  <div>
    <AuthorProfile />
  </div>
  <div>
    <ToDo />
  </div>
</template>

<style>

</style>
