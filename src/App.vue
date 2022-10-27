<template>
  <MainComponent :users="users" />
</template>

<script>
import {sampleData} from "./models/data.js";
import MainComponent from "./components/Main.vue";

export default {
  name: "App",
  components: {
    MainComponent,
  },
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.users = sampleData();
  },
};
</script>
