<template>
  <div class="home pa-6 pt-0">

    <list-tasks
      v-if="$store.state.tasks.length"
      flat/>

    <no-tasks
      v-else/>

    <button-done-sorting 
      v-if="$store.state.sorting"/>

  </div>
</template>

<script>


export default {
    name: 'Home',
    components: {
      'list-tasks': require('@/components/Todo/ListTasks.vue').
      default,
      'no-tasks': require('@/components/Todo/NoTasks.vue').
      default,
      'button-done-sorting': require('@/components/Todo/ButtonDoneSorting.vue').
      default,
    }
};
</script>

