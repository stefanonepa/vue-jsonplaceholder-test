<template>
  <div id="app">
    <h1>UserID: {{userId}}</h1>
    <button @click="fetch">reload</button>
    <posts :postsData="posts" @remove="removePost"></posts>
  </div>
</template>

<script>
import Posts from './components/Posts'
import axios from 'axios'

export default {
  name: 'app',
  components: {
    Posts
  },
  data () {
    return {
      posts: [],
      userId: 1
    }
  },
  methods: {
    removePost (index) {
      this.posts = this.posts.filter((x, i) => i !== index)
      // this.posts.splice(index, 1)
    },
    fetch () {
      let that = this
      axios.get('https://jsonplaceholder.typicode.com/posts?userId=' + that.userId)
      .then(function (response) {
        that.posts = response.data.map((post) => {
          post.showDetails = false
          post.showComments = false
          post.comments = []
          return post
        })
      })
      .catch(function (error) {
        console.log(error)
      })
    }
  },
  created () {
    this.fetch()
  }
}
</script>
