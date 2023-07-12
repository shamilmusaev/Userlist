<template>
  <div>
    <Vendre/>
    <UserList />
  </div>
</template>

<script>
import UserList from "./components/UserList.vue";
import Vendre from "./components/Vendre.vue";

export default {
  name: "App",
  components: {
    UserList,
    Vendre
    
    
  },
};
</script>

<style></style>
