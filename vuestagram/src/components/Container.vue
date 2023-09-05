<template>
  <div> 
    <Post :instadata="instadata[i]" v-for="(a,i) in instadata" :key="a"/>
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