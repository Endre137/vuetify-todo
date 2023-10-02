<template>
    <v-text-field
      v-model="newTaskTitle"
      @keyup.enter = "addTask()"
      class="field-add-task pa-4"
      outlined
      placeholder="Add Task"
      clearable
    >
    <template v-slot:append>
      <v-icon @click="addTask"
      color="green darken-1"
      :disabled="newTaskTitleInvalid"
      >mdi-plus</v-icon>
    </template>
    </v-text-field>
</template>

<script>
export default{
    data() {
        return {
          newTaskTitle: '',

        };
    },
    computed:{
      newTaskTitleInvalid(){
        return !this.newTaskTitle
      }
    },
    methods: {
      addTask(){
        if(!this.newTaskTitleInvalid){
        this.$store.dispatch('addTask', this.newTaskTitle)
        this.newTaskTitle = ''
        }
      }
    }
}
  
</script>

<style>
.field-add-task.v-input--is-focused.v-input__color{

  background: black;
}
</style>
