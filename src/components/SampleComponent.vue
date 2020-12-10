<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="8">
        <v-text-field v-model="taskMessage"
          label="Task Description"
        ></v-text-field>
      </v-col>
      <v-col cols="2">
        <v-btn :disabled="taskMessage == '' " @click="addTaskToList()">Add Task</v-btn>
      </v-col>
      <v-col cols="2">
        <v-select
          :items="taskPriorities"
          label="Priority"
          v-model="selected"
        ></v-select>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class SampleComponent extends Vue{
  taskMessage = "";
  taskPriorities = ["Low", "High"]
  selected = "Low"
  

  // methods
  addTaskToList(): void{
    const payload = {message: this.taskMessage, priority: this.selected};
    this.$root.$emit('addToList', payload);
  }
}
</script>
