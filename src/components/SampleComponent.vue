<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="8">
        <v-text-field v-model="taskMessage"
          label="Task Description"
        ></v-text-field>
      </v-col>
      <v-col cols="4">
        <v-btn :disabled="taskMessage == '' " @click="addTaskToList()">Add Task</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class SampleComponent extends Vue{
  taskMessage = "";

  // methods
  addTaskToList(): void{
    this.$root.$emit('addToList', this.taskMessage);
  }
}
</script>
