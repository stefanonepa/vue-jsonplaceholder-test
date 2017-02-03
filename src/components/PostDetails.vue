<template>
  <div class="postDetails">
    <div>PostId: {{postData.id}}</div>
    <div>Body: {{postData.body}}</div>
    <div class="postDetails--commentlink" @click="showComments = !showComments">Comments: {{ comments.length }}</div>
    <transition name="fade">
      <comments :commentsData="comments" v-if="showComments"></comments>
    </transition>
  </div>
</template>
<script>
  import Comments from './Comments'
  import axios from 'axios'

  export default {
    props: ['postData'],
    components: {Comments},
    data () {
      return {
        comments: [],
        showComments: false
      }
    },
    mounted () {
      let that = this
      axios.get('https://jsonplaceholder.typicode.com/comments?postId=' + that.postData.id)
      .then(function (response) {
        that.comments = response.data
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