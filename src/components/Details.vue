<template >
  <h1>{{ user.id }}</h1>

  <p>
    {{ this.format(Date.now(user.created), "MMMM dd, yyyy, h:mm a") }} -
    <span> {{ user.location }}</span>
  </p>

  <ol>
    <li v-if="user.devices || user.devices == 0">
      <h4>Devices</h4>
      <span>{{ user.devices }}</span>
    </li>
    <li v-if="user.sessions && user.sessions.length">
      <h4>Sessions</h4>
      <span>{{ user.sessions.length }}</span>
    </li>
    <li v-if="user.events || user.events == 0">
      <h4>Events</h4>
      <span>{{ user.events }}</span>
    </li>
  </ol>
  <table>
    <thead>
      <tr>
        <th>Attribute</th>
        <th>Value</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(value, key, index) in user.attributes" :key="`${index}`">
        <td>{{ key }}</td>
        <td>{{ value }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import { format } from "date-fns";

export default {
  name: "UserDetails",
  props: {
    user: Object,
  },
  data() {
    return {
      format,
    };
  },
  watch: {
    users: function () {},
  },
};
</script>
