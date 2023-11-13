<template>
  <div class="card">
    <div class="imgBg">
      <img :src="prodProp.images[0].src" alt="" />
    </div>
    <div class="animContent">
      <div class="content">
        <span class="prodName">{{ prodProp.title }}</span>
        <span class="price">${{ prodProp.variants[0].price }}</span>
      </div>
      <div class="buy">
        <div class="row">
          <a href="#" class="btn2" @click="addToCart">Add to Cart</a>
          <button @click="showModal = true" class="button moreInfo">More Info</button>
        </div>
      </div>
    </div>
    <div>
      <transition name="fade" appear>
        <div class="modal-overlay" v-if="showModal" @click="showModal = false"></div>
      </transition>
      <transition name="pop" appear>
        <div class="modal" role="dialog" v-if="showModal">
          <div class="modalContent">
            <div>
              <img :src="prodProp.images[0].src" alt="" />
            </div>
            <div>
              <h1>{{ prodProp.title }}</h1>
              <p v-html="prodProp.body_html"></p>
              <div class="cart">
                <div class="quantity">
                  <div class="add"  @click="qualityChange('increase')">
                    <img src="../assets/plus.png" alt="" />
                  </div>
                  <input
                    class="inputBox"
                    type="number"
                    inputmode="numeric"
                    v-model="inputValue"
                    @input="validateInput"
                  />
                  <div class="subtract" @click="qualityChange('decrease')">
                    <img src="../assets/minus-sign.png" alt="" />
                  </div>
                </div>
                <button @click="addToCart" class="button">Add to Cart</button>
              </div>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    prodProp: String
  },
  data() {
    return {
      showModal: false,
      inputValue: 1,
      quality: 1
    }
  },
  methods: {
    validateInput() {
      if(this.inputValue){
        this.quality = this.inputValue
      }
      else {
        this.inputValue = this.quality
      }

      console.log(this.quality);
    },

    qualityChange(mode) {

      if(mode === "increase")
      {
        this.quality += 1
        this.inputValue += 1
      }
      else {
        this.quality -= 1
        this.inputValue -= 1
      }

    },
    addToCart() {
      alert("This store does not exist");
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');
.card {
  position: relative;
  width: 330px;
  height: 100%;
  margin: 10px;
  background: #fff;
  border-radius: 10px;
  box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.318);
}

.card .imgBg {
  position: relative;
  width: 100%;
  z-index: 0;
}

.card .imgBg img {
  width: 100%;
  height: 100%;
  border-radius: 15px;
  z-index: -99;
  transition: all 0.5s ease-in-out;
}

.card .content {
  font-family: Poppins, sans-serif;
  display: flex;
  flex-direction: column;
  padding: 0px 20px;
  margin-top: -20px;
  bottom: 0;
  width: 90%;
  transition: all 0.6s ease-in-out;
}

.card .content .prodName {
  font-size: 22px;

  font-weight: 600;
  z-index: 1;
}

.card .content .price {
  font-size: 18px;
  font-weight: 400;
  color: #000000;
}

.card:hover .content {
  transform: translateY(-40px) rotateX(90deg);
  opacity: 0;
}

.buy {
  position: absolute;
  display: flex;
  width: 100%;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  bottom: 0;
  margin-bottom: 10px;
  opacity: 0;
  transform: translateY(40px) rotateX(-90deg);
  transition: all 0.6s ease-in-out;
}

.card:hover .buy {
  transform: translateY(0px) rotateX(0deg);
  opacity: 1;
}

.row {
  display: flex;
  justify-content: center;
  margin: 5px 0px;
}

.buy a {
  font-family: Poppins, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 120px;
  height: 40px;
  border-radius: 10px;
  background: #fd7b3a;
  color: #fff;
  font-size: 16px;
  padding: 0px 10px;
  margin: 0px 5px;
  font-weight: 300;
  text-decoration: none;
  transition: all 0.5s ease-in-out;
}

.buy .button,
.modal .button {
  border: none;
  font-family: Poppins, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 120px;
  height: 40px;
  border-radius: 10px;
  background: #fd7b3a;
  color: #fff;
  font-size: 16px;
  padding: 0px 10px;
  margin: 0px 10px;
  font-weight: 300;
  text-decoration: none;
  transition: all 0.5s ease-in-out;
  cursor: pointer;
}

.cart {
  display: flex;
  /* justify-content: space-between; */
  align-items: center;
}

.quantity {
  position: relative;
}

.cart .quantity img {
  position: absolute;
  width: 10px;
}

.quantity .add img {
  right: 15px;
  top: 35%;
}
.quantity .subtract img {
  left: 15px;
  top: 35%;
}
.cart .inputBox {
  border: none;
  outline: none;
  font-family: Poppins, sans-serif;
  font-weight: 300;
  font-size: 16px;
  max-width: 50px;
  text-align: center;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

.cart .quantity {
  border: 2px solid #424242;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 30%;
  height: 30px;
}

.buy .moreInfo {
  background: #fff;
  color: #fd7b3a;
  border: 1px solid #fd7b3a;
}

.modal {
  position: absolute;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  text-align: center;
  font-family: Poppins, sans-serif;
  width: fit-content;
  height: fit-content;
  max-width: 50em;
  padding: 2rem;
  border-radius: 1rem;
  box-shadow: 0 5px 5px rgba(0, 0, 0, 0.2);
  background: #fff;
  z-index: 999;
  transform: none;
}
.modalContent {
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal img {
  width: 100%;
}

.modal h1 {
  margin: 0 0 1rem;
  font-size: 2rem;
  text-align: left;
  font-weight: 500;
}

.modal p {
  margin: 0 0 1rem;
  font-size: 16px;
  text-align: justify;
  font-weight: 300;
}

.modal img {
  width: 100%;
}

.modal-overlay {
  content: '';
  position: absolute;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 998;
  background: #2c3e50;
  opacity: 0.6;
  cursor: pointer;
}

/* ---------------------------------- */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.4s linear;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.pop-enter-active,
.pop-leave-active {
  transition:
    transform 0.4s cubic-bezier(0.5, 0, 0.5, 1),
    opacity 0.4s linear;
}

.pop-enter,
.pop-leave-to {
  opacity: 0;
  transform: scale(0.3) translateY(-50%);
}
</style>
