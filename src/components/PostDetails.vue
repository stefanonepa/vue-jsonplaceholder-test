<template>
  <div class="postDetails">
    <div>PostId: {{postData.id}}</div>
    <div>Body: {{postData.body}}</div>
    <div class="postDetails--commentlink" @click="postData.showComments = !postData.showComments">Comments: {{ postData.comments.length }}</div>
    <transition name="fade">
      <comments :commentsData="postData.comments" v-if="postData.showComments"></comments>
    </transition>
  </div>
</template>
<script>
  import Comments from './Comments'
  import axios from 'axios'

  export default {
    props: ['postData'],
    components: {Comments},
    mounted () {
      let that = this
      axios.get('https://jsonplaceholder.typicode.com/comments?postId=' + that.postData.id)
      .then(function (response) {
        that.postData.comments = response.data
        // that.comments = response.data
      })
      .catch(function (error) {
        console.log(error)
      })
    }
  }
</script>
<style>
  .postDetails:hover{
    background-color: #eef;
  }
  .postDetails{
    background-color: #eef;
  }
  .postDetails--commentlink{
    background-color: #efe;
    padding: 0.3em 0 0.3em 0;
    font-size: 1.1em;
  }
  .postDetails--commentlink:hover{
    cursor:pointer;
  }
</style>