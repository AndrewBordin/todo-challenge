<template>
  <v-container>
      <v-list
      subheader
      two-line
      flat
      >
      <v-subheader>Tasks to-do</v-subheader>
        <v-list-item-group
            multiple >
            <v-for v-for="task in UnCompletedTasks" :key="task.id">
              <!-- Component Here -->
              <TaskItem :task="task" @clicked-show-detail="clickedShowDetailModal"/>
            </v-for>
        </v-list-item-group>
      </v-list>
      <v-list
      subheader
      two-line
      flat
      >
      <v-subheader>Completed Tasks</v-subheader>
        <v-list-item-group
            multiple>
            <span v-for="task in CompletedTasks" :key="task.id">
              <!-- Component Here -->
              <TaskItem :task="task" @clicked-show-detail="clickedShowDetailModal"/>
            </span>
        </v-list-item-group>
      </v-list>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import TaskItem from './TaskItem.vue'

@Component({
  components: {
    TaskItem
  }
})
export default class List extends Vue {
  // Data
  currentDate = new Date().toLocaleString()
  tasks = [
    {
      id: 0,
      name: 'Task 1',
      isCompleted: false,
      dateOfCreation: this.currentDate
    },
    {
      id: 1,
      name: 'Task 2',
      isCompleted: false,
      dateOfCreation: this.currentDate
    },
  ]


  // Computed
  get CompletedTasks() {
    return this.tasks.filter(task => {
      return task.isCompleted == true
    })
  }

  get UnCompletedTasks() {
    return this.tasks.filter(task => {
      return task.isCompleted == false
    })
  }

  // methods
  clickedShowDetailModal (value) {
    for(var i = 0; i < this.tasks.length; i++) {
      if(this.tasks[i].id == value.id) {
          this.tasks.splice(i, 1);
          break;
      }
    }
  }

  mounted(){
    this.$root.$on('eventing', data => {
      var d = new Date();
      let dataObj = {id:new Date().getTime(), name: data, isCompleted: false, dateOfCreation: d.toLocaleString()}
      this.tasks.push(dataObj)
    });
  }
}
</script>