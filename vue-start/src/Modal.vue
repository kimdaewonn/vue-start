<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image">
      <h4>{{원룸들[누른거].title}}</h4>
      <p>{{원룸들[누른거].content}}</p>
      <!-- <input @input="month = $event.target.value"> -->
      <input v-model.number="month">
      <p> {{month}}개월 선택함 : {{원룸들[누른거].price * month}}원</p>
      <button @click="modalclosefun" class="close">닫기</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Modal',
  data() {
    return {
      month : 1,
    }
  },
  watch : {
    month(a) {
      if(isNaN(a) === true ){
        alert('숫자만입력해라')
        this.month = 1;
      }
      
    }
  },
  props: {
    원룸들 : Array,
    누른거 : Number,
    모달창열렸니 : Boolean,
  },
  methods: {
    modalclosefun() {
      this.$emit('closeModal')
    }
  },
  updated(){
    if(this.month == 2) {
      // alert('2개월은 너무적음')
    }
    if(this.month == 24) {
      this.month = 2
    }
    
  }
  
}
</script>

<style>

</style>