<template>
  <div>
    <h2>Posts</h2>
    <div>
      <post :postData="post" @remove="remove(index)" v-for="(post, index) in postsData"></post>
    </div>
  </div>
</template>
<script>
  import Post from './Post'
  export default {
    props: ['postsData'],
    components: {Post},
    methods: {
      remove (index) {
        this.$emit('remove', index)
      }
    }
  }
</script>