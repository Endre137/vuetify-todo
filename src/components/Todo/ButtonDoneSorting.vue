<template>
  <v-btn
  @click="$store.commit('toggleSorting')"
  class="button-done-sorting"
  color="green darken-1">
    Done Sorting
  </v-btn>
</template>

<script>
export default {

}
</script>

<style>
.button-done-sorting{
    position:relative;
    bottom: 20px;
    left: 50px;
    margin: 50px
}
</style>