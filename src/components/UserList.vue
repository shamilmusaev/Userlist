<template>
  <div class="userlist-cont">
    <h1 class="userlist-title">Våra experter</h1>
    <p class="userlist-par">
      Har du en fråga om en specifik del i vår verksamhet? Kontakta en av våra
      experter.
    </p>
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
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    
}

.pagination {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.page {
  padding: 8px;
  border: solid 1px black;
  margin-right: 10px;
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
