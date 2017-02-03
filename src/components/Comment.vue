<template>
  <div class="comment">
    <div>
      Email: {{commentData.email}}
    </div>
    <div>
      Name: {{commentData.name}}
    </div>
    <div>
      Body: {{commentData.body}}
    </div>
  </div>
</template>
<script>
  export default {
    props: ['commentData']
  }
</script>
<style>
  .comment{
    background-color: #fee;
    border: 0.1em solid #ddd;
    margin: 0.3em 0 0.3em 0;
  }
</style>