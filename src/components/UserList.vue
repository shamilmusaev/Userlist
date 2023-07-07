<template>
  <div>
    <ul>
      <li v-for="(user, index) in users" :key="index">
        <UserCard
          :firstName="user.first_name"
          :lastName="user.last_name"
          :imgUrl="user.avatar"
          :email="user.email"
        />
      </li>
      <li v-for="(user2, index) in users2" :key="index">
        <UserCard
          :firstName="user2.first_name"
          :lastName="user2.last_name"
          :imgUrl="user2.avatar"
          :email="user2.email"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import UserCard from "./UserCard.vue";
import axios from "axios";
export default {
  name: "UserList",
  components: {
    UserCard,
  },
  data() {
    return {
      users: [],
      users2: [],
    };
  },
  mounted() {
    axios
      .get("https://reqres.in/api/users")
      .then((response) => (this.users = response.data.data));
    axios
      .get("https://reqres.in/api/users?page=2")
      .then((response) => (this.users2 = response.data.data));
  },
};
</script>

<style></style>
