<template>
  <div>
    <h5>{{블로그글[0].title}}</h5>
    <h5>{{블로그글[0].date}}</h5>
  </div>
  <div>
    <h5>{{블로그글[1].title}}</h5>
    <h5>{{블로그글[1].date}}</h5>
  </div>
  <div>
    <h5>{{블로그글[2].title}}</h5>
    <h5>{{블로그글[2].date}}</h5>
  </div>
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