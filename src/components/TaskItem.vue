<template>
  <v-container>
    <v-list-item @click="task.isCompleted ? task.isCompleted = false : task.isCompleted = true">
      <template>
        <v-btn
          elevation="2"
          icon
          medium
          outlined
          raised
          rounded
          class="mr-2"
          color="red"
          @click.capture.stop="deleteTask(task)"
        > 
          <span class="mdi mdi-delete"></span>
        </v-btn>
        <v-list-item-content>
          <v-list-item-title>{{task.name}}</v-list-item-title>
        </v-list-item-content>
        <v-list-item-action>
          <v-checkbox v-model="task.isCompleted"></v-checkbox>
        </v-list-item-action>
      </template>
    </v-list-item>
  </v-container>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class TaskItem extends Vue{
  // Props
  @Prop({ default: "Task Name" }) task: Record<string, boolean>;

  // Data

  // Computed


  // methods
  deleteTask(task) {
    console.log(task.id)
    this.$emit('clicked-show-detail', task);
  }

  // lifecycle hooks
  created(){
    console.log("[SampleComponent.vue] created");
  }
  mounted(){
    console.log("[SampleComponent.vue] mounted");
  }
  updated(){
    console.log("[Task.vue] updated");
  }
  destroyed(){
    console.log("[SampleComponent.vue] destroyed");
  }
}
</script>
