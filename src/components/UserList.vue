<template>
  <div>
    <ul>
      <li class="list" v-for="(user, index) in users" :key="index">
        <UserCard
          :firstName="user.first_name"
          :lastName="user.last_name"
          :imgUrl="user.avatar"
          :email="user.email"
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
