<template>
  <div class="container">
    <div class="card">
      <div class="blob"></div>
      <span class="img"><img :src="imgUrl" alt="" /></span>
      <h2>
        {{ firstName }}<br /><span>{{ lastName }}</span>
      </h2>

      <!-- Кнопка для открытия модального окна -->
      <button class="contact-btn" @click="openModal">Contact</button>

      
      <div v-if="showModal" class="modal">
        <div class="modal-content">
          
          
          <p>EMAIL: <br> {{ email }}</p>

          
          <button @click="closeModal">Close</button>
        </div>
      </div>
    </div>

    <!-- ================= -->
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
      showModal: false, // Состояние модального окна
    };
  },
  methods: {
    openModal() {
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
    },
  },
};
</script>

<style>
/* =========== */

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5); /* Затемнение фона */
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background-color: white;
  padding: 20px;
  border-radius: 5px;
}

/* Дополнительные стили по вашему выбору */

li {
  list-style: none;
}
ul {
  margin-top: 30px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-row-gap: 40px;
}
.email {
  color: white;
  font-size: 14px;
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
  background: white;
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
  width: 85%;
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
  transition: transform 1s; 
  transform-origin: center center;
}

.card:hover .img {
  width: 100%;
  height: 70%;

  border-radius: 10px 0 0;
  margin: 0 auto;
  background-color: #f0f0f0;
  z-index: 99999
}



/* .card .img {
  display: flex;
  margin: 30px auto 10px auto;
  width: 70px;
  height: 70px;
  background-color: #4bb8ff;
  border-radius: 50%;
  font-size: 11px;
  justify-content: center;
  align-items: center;
  transition: transform 0.5s; 
  transform-origin: center center; 
}

.card:hover .img {
  transform: scale(1.1); 
} */

/* =========== */

.card:hover img {
  transform: scale(1.1);
}

.card:hover .contact-btn {
  font-size: 13px;
  background: #f0f0f0;
  color: black;
  cursor: pointer;
  position: relative;
  bottom: 10px;
  box-shadow: 0 0 20px 1px rgba(0, 0, 0, 0.623);
}

.card:hover .contact-btn:hover {
  background-color: white;
  color: black;
}

.card:hover .email {
  font-size: 15px;
}



.card h2 {
  padding: 15px 10px;
  font-size: 20px;
  font-weight: 100;
  transition: all 0.1s;
  z-index: -99;
  line-height: 17px;
  height: 34px; /* Добавлено фиксированное значение высоты */
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
