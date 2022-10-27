<template>
  <li @click="handleClick(user)" v-bind:class="{ active: selected == user.id }">
    <h3>{{ user.id }}</h3>
    <p>
      <span>{{ user.devices }} Devices</span> -
      <span>{{ user.sessions.length }} Sessions</span> -
      <span>{{ user.location }}</span>
    </p>
  </li>
</template>


<script>
export default {
  name: "UsersList",
  props: {
    user: Object,
    selected: String,
  },
  data() {
    return {
      activeId: 0,
    };
  },
  methods: {
    handleClick(u) {
      this.$emit("customSelect", u);
    },
  },
};
</script>
