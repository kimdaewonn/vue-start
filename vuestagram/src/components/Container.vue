<template>
  <div> 
    <div v-if="step == 0">
      <Post :instadata="instadata[i]" v-for="(a,i) in instadata" :key="a"/>
    </div>

      <!-- 필터선택페이지 -->
    <div v-if="step == 1">
      <div :class="선택한필터"  class="upload-image" :style="`background-image:url(${이미지})`"></div>
      <div class="filters">
        <FilterBox :필터="필터" :이미지="이미지" v-for="필터 in 필터들" :key="필터" >
          <span>{{필터}}</span>
        </FilterBox>
      </div>
    </div>


    <!-- 글작성페이지 -->
    <div v-if="step == 2">
      <div :class="선택한필터" class="upload-image" :style="`background-image:url(${이미지})`"></div>
      <div class="write">
        <textarea @input="write" class="write-box">write!</textarea>
      </div>
    </div>

  </div>
</template>

<script>
import Post from './Post.vue';
import FilterBox from './FilterBox.vue';

export default {
data(){
  return {
    필터들 :[ "aden", "_1977", "brannan", "brooklyn", "clarendon", "earlybird", "gingham", "hudson", 
    "inkwell", "kelvin", "lark", "lofi", "maven", "mayfair", "moon", "nashville", "perpetua", 
    "reyes", "rise", "slumber", "stinson", "toaster", "valencia", "walden", "willow", "xpro2"],
    선택한필터 : '',
  }
},
mounted(){
  this.emitter.on('filterClick',(a)=>{
    this.선택한필터 = a
    
  });
},
props: {
  instadata: Array,
  step:Number,
  이미지:String,
  
},

components: {
  Post,
  FilterBox,
},
methods: {
  write(e){
    this.$emit('write',e.target.value)
  },

},

}
</script>

<style>
.upload-image{
width: 100%;
height: 450px;
background: cornflowerblue;
background-size : cover;
}
.filters{
overflow-x:scroll;
white-space: nowrap;
}
.filter-1 {
width: 100px;
height: 100px;
background-color: cornflowerblue;
margin: 10px 10px 10px auto;
padding: 8px;
display: inline-block;
color : white;
background-size: cover;
}
.filters::-webkit-scrollbar {
height: 5px;
}
.filters::-webkit-scrollbar-track {
background: #f1f1f1; 
}
.filters::-webkit-scrollbar-thumb {
background: #888; 
border-radius: 5px;
}
.filters::-webkit-scrollbar-thumb:hover {
background: #555; 
}
.write-box {
border: none;
width: 90%;
height: 100px;
padding: 15px;
margin: auto;
display: block;
outline: none;
}
</style>