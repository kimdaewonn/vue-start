<template>
  <div v-for="(a,i) in instadata" :key="a"> 
    <Post :instadata="instadata[i]"/>
  </div>
</template>

<script>
import Post from './Post.vue';

export default {
props: {
  instadata: Array,
},

components: {
  Post,
}

}
</script>

<style>
</style>