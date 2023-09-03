<template>
  <div>
    <Post :instadata="instadata"/>
    <Post :instadata="instadata"/>
    <Post :instadata="instadata"/>
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