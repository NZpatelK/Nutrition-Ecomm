<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="navHeader">
    <div class="wrapper">
      <img class="logo" src="./assets/brand.png" alt=""/>
      <nav>
        <RouterLink class="navLink" to="/">Home</RouterLink>
        <!-- <RouterLink class="navLink" to="/about">About</RouterLink> -->
        <RouterLink class="navLink" to="/products">Products</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');

.navHeader {
  display: flex;
  justify-content: center;
  width: 100%;
  overflow-x: hidden;
}

.wrapper {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  border-radius:50px;
  padding: 10px 0;
  width: 80%;
  transform: translateY(-100%);
  opacity: 0;
  margin: 20px auto;
  backdrop-filter: blur(10px);
  animation: fadeIn 1s 1s ease-in-out forwards;
}


.logo{
  width: 100px;
  margin-right: 50px;
}


nav .navLink {
  text-decoration: none;
  font-family: 'Poppins', sans-serif;
  font-weight: 300 !important;
  font-size: 20px;
  font-weight: bold;
  color: #000;
  padding: 10px;
  color: #fff;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
    transform: translateY(-100%);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

</style>
