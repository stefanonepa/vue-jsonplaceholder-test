<template>
  <div>
    <comment v-for="comment in commentsData" :commentData="comment"></comment>
  </div>
</template>
<script>
  import Comment from './Comment'
  export default {
    props: ['commentsData'],
    components: {Comment}
  }
</script>