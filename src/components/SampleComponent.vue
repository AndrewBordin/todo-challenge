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
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class SampleComponent extends Vue{
  // Props

  // Data
  message = "";

  // Computed


  // methods
  addTaskToList(): void{
    this.$root.$emit('eventing', this.message);
  }

  // lifecycle hooks
  created(){
    console.log("[SampleComponent.vue] created");
  }
  mounted(){
    console.log("[SampleComponent.vue] mounted");
  }
  updated(){
    console.log("[SampleComponent.vue] updated");
  }
  destroyed(){
    console.log("[SampleComponent.vue] destroyed");
  }
}
</script>
