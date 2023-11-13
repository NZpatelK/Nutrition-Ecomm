<template>
  <main>
    <section class="homepage">
      <div class="infoContent slide-in-elliptic-left-fwd">
        <div class="topProdTitle">
          <h2>Top Products</h2>
          <h1>{{ productData.products[0].title }}</h1>

          <div class="priceContainer">
            <p class="price">${{ productData.products[0].variants[0].price }}</p>
            <button @click="addToCart">Add To Cart</button>
          </div>

          <p v-html="productData.products[0].body_html"></p>
        </div>
      </div>

      <div class="imgContent slide-in-elliptic-right-bck">
        <img class="animImg choc" src="../assets/chcoc.png" alt="" />
        <img class="animImg lollie" src="../assets/image-removebg-preview (1).png" alt="" />
        <img class="prod" src="../assets/pepperImg.png" alt="" />
      </div>
    </section>
  </main>
</template>

<script>
import prodData from '../data/bulletproofProduct.json'

export default {
  data() {
    return {
      productData: prodData
    }
  },
  methods: {
    addToCart() {
      alert("This store does not exist");
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');

.homepage {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  padding: 0 40px;
  margin: 100px 0;
  height: 100%;
}

.infoContent {
  font-family: 'Poppins', sans-serif;
  width: 40%;
}

.infoContent::before {
  content: '';
  position: absolute;
  top: 20%;
  left: 40%;
  border-radius: 100%;
  width: 500px;
  height: 500px;
  background: #ffa477;
  filter: blur(80px);
  z-index: -9999;
}

.homepage h1,
h2 {
  color: #fff;
}

.priceContainer {
  display: flex;
  align-items: center;
  margin-top: 10px;
  /* justify-content: center; */
}

.price {
  color: #ffffff;
  font-size: 20px !important;
  font-weight: 300 !important;
  margin: 0;
  padding: 0;
}

.homepage button {
  background: #ffa477;
  color: #fff;
  font-size: 14px;
  font-weight: 500;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-left: 15px;
  transition: 0.3s;
}

.homepage button:hover {
  transform: scale(1.1);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.homepage h1 {
  font-size: 28px;
  padding: 0;
  margin: 0;
}

.homepage h2 {
  font-size: 22px;
  transition: 0.3s;
}

.infoContent p {
  text-align: justify;
  font-size: 14px;
}

.homepage .prod {
  width: 100%;
  margin-left: 40px;
  transform: rotate(16deg);
  filter: drop-shadow(20px 20px 30px rgba(0, 0, 0, 0.392));
  animation: rotateImg 1s linear;
}

.animImg {
  position: absolute;
  width: 50% !important;
}

.choc {
  top: 20%;
  left: 30%;
  transform: rotate(-73deg) !important;
  animation: chocAnim 1s 0.5s forwards;
}

@keyframes chocAnim {
  0% {
    top: 20%;
    left: 30%;
    transform: rotate(-73deg) scale(0.5) !important;
  }
  100% {
    top: 56%;
    left: 57%;
    transform: rotate(-73deg) scale(1) !important;
  }
}

.lollie {
  top: 20%;
  left: 30%;
  transform: rotate(0deg) !important;
  animation: lollieAnim 1s 0.5s forwards;
}

@keyframes lollieAnim {
  0% {
    top: 20%;
    left: 30%;
    transform: rotate(0deg) !important;
  }
  100% {
    top: -3%;
    left: -3%;
    transform: rotate(0deg) !important;
  }
}

@keyframes rotateImg {
  from {
    transform: rotate(-45deg);
  }
  to {
    transform: rotate(16deg);
  }
}

.slide-in-elliptic-left-fwd {
  -webkit-animation: slide-in-elliptic-left-fwd 1s 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  animation: slide-in-elliptic-left-fwd 1s 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}

@-webkit-keyframes slide-in-elliptic-left-fwd {
  0% {
    -webkit-transform: translateX(-800px) rotateY(30deg) scale(0);
    transform: translateX(-800px) rotateY(30deg) scale(0);
    -webkit-transform-origin: -100% 50%;
    transform-origin: -100% 50%;
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0) rotateY(0) scale(1);
    transform: translateX(0) rotateY(0) scale(1);
    -webkit-transform-origin: 1800px 50%;
    transform-origin: 1800px 50%;
    opacity: 1;
  }
}
@keyframes slide-in-elliptic-left-fwd {
  0% {
    -webkit-transform: translateX(-800px) rotateY(30deg) scale(0);
    transform: translateX(-800px) rotateY(30deg) scale(0);
    -webkit-transform-origin: -100% 50%;
    transform-origin: -100% 50%;
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0) rotateY(0) scale(1);
    transform: translateX(0) rotateY(0) scale(1);
    -webkit-transform-origin: 1800px 50%;
    transform-origin: 1800px 50%;
    opacity: 1;
  }
}

.slide-in-elliptic-right-bck {
  -webkit-animation: slide-in-elliptic-right-bck 1s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  animation: slide-in-elliptic-right-bck 1s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}

@-webkit-keyframes slide-in-elliptic-right-bck {
  0% {
    -webkit-transform: translateX(800px) rotateY(30deg) scale(6.5);
    transform: translateX(800px) rotateY(30deg) scale(6.5);
    -webkit-transform-origin: -100% 50%;
    transform-origin: -100% 50%;
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0) rotateY(0) scale(1);
    transform: translateX(0) rotateY(0) scale(1);
    -webkit-transform-origin: 600px 50%;
    transform-origin: 600px 50%;
    opacity: 1;
  }
}
@keyframes slide-in-elliptic-right-bck {
  0% {
    -webkit-transform: translateX(800px) rotateY(30deg) scale(6.5);
    transform: translateX(800px) rotateY(30deg) scale(6.5);
    -webkit-transform-origin: -100% 50%;
    transform-origin: -100% 50%;
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0) rotateY(0) scale(1);
    transform: translateX(0) rotateY(0) scale(1);
    -webkit-transform-origin: 600px 50%;
    transform-origin: 600px 50%;
    opacity: 1;
  }
}

@media screen and (max-width: 1200px){

  .homepage{
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    justify-content: center;
    height: 100%;
  }

  .infoContent{
    width: 80%;
  }
}

@media screen and (max-width: 500px){
    .infoContent{
    width: 95%;
  }

  .homepage h1 {
  font-size: 22px;
  padding: 0;
  margin: 0;
}

.homepage h2 {
  font-size: 18px;
  transition: 0.3s;
}

.infoContent p {
  text-align: justify;
  font-size: 12px;
}

}
</style>
