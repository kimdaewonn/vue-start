<template>
  <transition name="fade">
    <Modal @closeModal = "모달창열렸니 = false" 
    :원룸들="원룸들" :누른거="누른거"
    :모달창열렸니="모달창열렸니"/>
  </transition>

  <div class="menu">
    <a v-for="(a) in 메뉴들" :key="a" href="#">{{a}}</a>
  </div>

  <Discount :discountNumber = discountNumber
  v-if="showDiscount == true"/>

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>
  <button @click="titleSort">알파벳순정렬</button>
  
  <Card @openModal = "모달창열렸니 = true; 누른거 = $event"
  v-for="(작명,i) in 원룸들" :key="작명" :원룸="원룸들[i]"/>


</template>

<script>
import apidata from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';




export default {
  name: 'App',
  data(){
    return {
      showDiscount : true,
      discountNumber : 30,
      원룸들오리지널 : [...apidata],
      오브젝트 : { name: 'kim', age: 20},
      누른거 : 0,
      원룸들 : apidata,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      메뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸','천호동원룸','마포구원룸'],
    }
  },
  methods : {
    increase() {
      this.신고수 += 1;
    },
    priceSort(){
      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    },
    titleSort(){
      this.원룸들.sort(function(a,b){
        return a.title < b.title ? -1 : a.title > b.title ? 1 : 0;
      })
    }
  },

  mounted(){
    setInterval(()=>{
      this.discountNumber -= 1
      if(this.discountNumber == 0){
        this.showDiscount = false
      }
    },1000)

  },


  
  updated(){

  },

  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
    // 오른쪽은 자유작명, es6 같으면 한글자로 축약가능
  }
}
</script>

<style>
.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}

.fade-leave-from {
  opacity: 0;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 1;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
