<template>
  <div>
    <h1>Posts</h1>
    <author-filter :authors="authors" :selected-author="selectedAuthor" @update:selectedAuthor="updateSelectedAuthor" />
    <post-list :posts="posts" :filteredPosts="filteredPosts" />
  </div>
</template>

<script>
import PostList from './components/PostList.vue';
import AuthorFilter from './components/AuthorFilter.vue';

export default {
  components: {
    PostList,
    AuthorFilter,
  },
  data() {
    return {
      posts: [],
      authors: [],
      selectedAuthor: '',
    };
  },
  computed: {
    filteredPosts() {
      if (!this.selectedAuthor) {
        return this.posts;
      }
      return this.posts.filter(post => post.userId === parseInt(this.selectedAuthor));
    },
  },
  mounted() {
    this.fetchPosts();
    this.fetchAuthors();
  },
  methods: {
    async fetchPosts() {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      this.posts = await response.json();
    },
    async fetchAuthors() {
      const response = await fetch('https://jsonplaceholder.typicode.com/users');
      this.authors = await response.json();
    },
    updateSelectedAuthor(newAuthorId) {
      this.selectedAuthor = newAuthorId;
    },
  },
  
};
</script>
