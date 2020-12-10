<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="8">
        <v-text-field v-model="message"
          label="Task Description"
        ></v-text-field>
      </v-col>
      <v-col cols="4">
        <v-btn @click="addTaskToList()">Add Task</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class SampleComponent extends Vue{
  // Data
  message = "";

  // methods
  addTaskToList(): void{
    this.$root.$emit('eventing', this.message);
  }
}
</script>
