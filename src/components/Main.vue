<template>
  <header>
    <h2>Users in Audience</h2>
    <p>Total users - Showing {{ users.length }} matching users</p>
  </header>
  <nav v-if="users.length">
    <ol>
      <UsersList
        v-for="user in users"
        :user="user"
        :key="user.id"
        :selected ="selected"
        @custom-select="handleCustomSelect"
      ></UsersList>
    </ol>
  </nav>
  <main>
    <UserDetails :user="user" />
  </main>
</template>

<script>
import UsersList from "./List.vue";
import UserDetails from "./Details.vue";

export default {
  name: "MainComponent",
  components: {
    UsersList,
    UserDetails,
  },
  props: {
    users: {
      type: Array,
    },
  },
  data() {
    return {
      user: {},
      selected: "",
    };
  },
  watch: {
    users: function () {
      this.user = this.users[0];
      this.selected = this.user.id;
    },
  },
  methods: {
    handleCustomSelect(u) {
      console.log(JSON.stringify(u));
      this.user = u;
      this.selected = this.user.id;
    },
  },
};
</script>
