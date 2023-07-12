<template>
  <div class="userlist-cont">
    <h1 class="userlist-title">Vi jobbar på Vendre</h1>

    <p></p>
    <ul>
      <li v-for="(user, index) in paginatedUsers" :key="index">
        <UserCard
          :firstName="user.first_name"
          :lastName="user.last_name"
          :imgUrl="user.avatar"
          :email="user.email"
        />
      </li>
    </ul>

    <div class="pagination">
      <div
        class="page"
        v-for="(page, index) in pages"
        :key="index"
        @click="pageClick(page)"
      >
        {{ page }}
      </div>
    </div>
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
      usersPerPage: 6,
      pageNumber: 1,
    };
  },
  methods: {
    pageClick(page) {
      this.pageNumber = page;
    },
  },
  computed: {
    pages() {
      return Math.ceil([...this.users, ...this.users2].length / 10);
    },
    paginatedUsers() {
      let from = (this.pageNumber - 1) * this.usersPerPage;
      let to = from + this.usersPerPage;
      return [...this.users, ...this.users2].slice(from, to);
    },
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

<style>
* {
  font-family: "Kumbh Sans", sans-serif;
}

body {
  background: linear-gradient(
    180deg,
    rgba(230, 199, 244, 1) 0%,
    rgba(244, 237, 254, 1) 35%,
    rgba(255, 255, 255, 1) 97%
  );
  background-repeat: no-repeat;
}
.pagination {
  margin-top: 70px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.page {
  padding: 8px;
  background-color: #4bb8ff;
  border-radius: 20%;
  color: white;
  border: solid 1px white;
  margin-right: 10px;
}

.page:hover {
  background-color: white;
  border: solid 1px black;
  color: black;
  transition: 1.5s;
}

.page {
  cursor: pointer;
}

.userlist-title,
.userlist-par {
  display: flex;
  justify-content: center;
  width: 100%;
}

.userlist-title {
  font-size: 30px;

  margin-top: 50px;
}

.userlist-par {
  font-size: 20px;
}

@media only screen and (max-width: 660px) {
  .userlist-title,
  .userlist-par {
    text-align: center;
    width: 100%;
    display: flex;
    justify-content: center;
  }
}
</style>
