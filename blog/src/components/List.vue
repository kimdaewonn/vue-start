<template>
  <div style="margin-top: 60px;" v-for="(a,i) in 블로그글" :key="a">
    <h5 @click="$router.push(`/detail/${i}`)">{{블로그글[i].title}}</h5>
    <h5>{{블로그글[i].date}}</h5>
  </div>


  <!-- <div style="margin-top: 60px;">
    <h5 @click="$router.push('/detail/0')">{{블로그글[0].title}}</h5>
    <h5>{{블로그글[0].date}}</h5>
  </div>
  <div>
    <h5 @click="$router.push('/detail/1')">{{블로그글[1].title}}</h5>
    <h5>{{블로그글[1].date}}</h5>
  </div>
  <div>
    <h5 @click="$router.push('/detail/2')">{{블로그글[2].title}}</h5>
    <h5>{{블로그글[2].date}}</h5>
  </div> -->


</template>

<script>
export default {
  name: "List",
  data(){

  },
  props: {
    블로그글 : Array,
  }

}
</script>

<style>

</style>