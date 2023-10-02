<template>
      <div
      class="noTasks">
      <div class="text-h5 green--text">
        <v-icon
          size="100"
          color="green"
        >
          mdi-check
        </v-icon>
        No Tasks
      </div>
    </div>
</template>


<style>
.noTasks{
  position:absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  opacity: 0.5;
}
</style>