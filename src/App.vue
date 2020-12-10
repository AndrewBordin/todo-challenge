<template>
  <v-app>
    <v-main>
      <SampleComponent />
      <List />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import SampleComponent from './components/SampleComponent.vue';
import List from './components/List.vue'

export default Vue.extend({
  name: 'App',

  components: {
    List,
    SampleComponent,
  },

  data: () => ({
    //
  }),
});
</script>
