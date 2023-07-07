<template>
  <div>
    <h1>Employee List</h1>
    <h2 v-for="(user, index) in users" :key="index">{{ user.first_name }}</h2>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "FetchTest",
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    axios
      .get("https://reqres.in/api/users")
      .then((response) => (this.users = response.data.data));
  },
};
</script>

<style></style>
