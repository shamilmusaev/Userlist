<template>
  <div class="container">
    <!-- <div class="user-card">
        <img :src="imgUrl" />
        <div class="user-card__info">
          <h2 class="name">{{ firstName }}</h2>
          <p class="contact">{{ email }}</p>
        </div>
      </div> -->

    <!-- ============ -->

    <div class="card">
      <div class="blob"></div>
      <span class="img"><img :src="imgUrl" alt="" /></span>
      <h2>{{ firstName }}<br /><span>{{ lastName }}</span></h2>
      <button class="contact-btn" @click="isEmailVisible = !isEmailVisible">
        Contact
      </button>
      <p class="email" v-if="isEmailVisible">{{ email }}</p>
    </div>

    <!-- ============ -->
  </div>
</template>

<script>
export default {
  name: "UserCard",
  props: {
    id: Number,
    imgUrl: String,
    firstName: String,
    lastName: String,
    email: String,
  },
  data() {
    return {
      isEmailVisible: false,
    };
  },
  methods: {},
};
</script>

<style>

.container{
    
}
li{
    list-style: none;
}
ul{
    margin-top: 100px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-row-gap: 40px;
    
    padding: 0;
    margin-left: 50px;
    margin-right: 50px;

    
}
.email {
  color: white;
  font-size: 16px;
  padding-bottom: 20px;
}

.contact-btn {
  width: auto;
  background-color: #4bb8ff;
  color: white;
  border: none;
  padding: 6px;
  border-radius: 20px;
}

img {
  border-radius: 60px;
}
.card {
  width: 190px;
  height: 254px;
  background: #f0f0f0;
  border-radius: 10px;
  text-align: center;
  transition: all 0.5s;
  margin-left: 20px;
}

.card:hover {
  box-shadow: 0 0 20px 1px rgba(0, 0, 0, 0.623);
  background-color: #4bb8ff;
}

.card .blob {
  height: 10px;
  width: 75%;
  border-radius: 0 0 30px 30px;
  margin: 0 auto;
  background-color: #4bb8ff;
  visibility: visible;
  transition: all 0.3s;
}

.card .img {
  display: flex;
  margin: 30px auto 10px auto;
  width: 70px;
  height: 70px;
  background-color: #4bb8ff;
  border-radius: 50%;
  font-size: 11px;
  justify-content: center;
  align-items: center;
  transition: all 0.5s;
}

.card:hover .img {
  width: 100%;
  height: 70%;
  border-radius: 10px 0 0;
  margin: 0 auto;
  background-color: #f0f0f0;
  z-index: 99999;
}

.card:hover .contact-btn {
  font-size: 16px;
  cursor: pointer;
}

.card h2 {
  padding: 15px 10px;
  font-size: 25px;
  transition: all 0.1s;
  z-index: -99;
  line-height: 17px;
}

.card span {
  font-size: 18px;
}

.card:hover h2 {
  opacity: 0;
  width: 100%;
  position: absolute;
  transition: all 0.5s;
}
</style>
