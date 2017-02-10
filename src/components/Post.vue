<template>
  <div class="post">
    <h2 @click="postData.showDetails = !postData.showDetails">{{postData.title}}</h2>
    <button @click="remove">remove</button>
    <transition name="fade">
      <post-details :postData="postData" v-if="postData.showDetails"></post-details>
    </transition>
  </div>
</template>
<script>
  import PostDetails from './PostDetails'

  export default {
    components: {PostDetails},
    props: ['postData'],
    methods: {
      remove () {
        this.$emit('remove')
      }
    }
  }
</script>
<style>
  .post{
    border-bottom: 0.1em solid #ddd;
    border-top: 0.1em solid #ddd;
    padding: 0.3em;
    margin: 0.3em;
  }
  .post > h2:hover{
    background-color: #eee;
    cursor:pointer;
  }
  .post > h2 {
    margin: 0.1em;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
    opacity: 0
  }
</style>