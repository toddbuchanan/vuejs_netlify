<template>
  <div class="bg-blue-900 h-24 shadow">
    <div class="text-3xl text-white p-8">ToDo's</div>
  </div>
  <div class="p-8">
    <ToDo />
  </div>
</template>

<script>
import ToDo from './components/ToDo.vue'
export default {
  name: 'App',
  components: {
    ToDo
  }
}
</script>

<style></style>
