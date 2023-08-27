<template>
    <div>
      <div v-for="post in filteredPosts" :key="post.id" class="post">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['posts', 'filteredPosts'],
  };
  </script>
  
  <style scoped>
  .post {
    margin: 20px;
    padding: 20px;
    border: 1px solid #ccc;
  }

  </style>
  