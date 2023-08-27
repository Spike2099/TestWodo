<template>
    <div>
      <select :value="selectedAuthor" @input="emitSelectedAuthor">
        <option value="">All Authors</option>
        <option v-for="author in authors" :key="author.id" :value="author.id">
          {{ author.name }}
        </option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    props: ['authors', 'selectedAuthor'],
    methods: {
      emitSelectedAuthor(event) {
        this.$emit('update:selectedAuthor', event.target.value);
      },
    },
  };
  </script>
  