<template>
  <div id="app">
      <div class="post" v-for="post in allPosts" :key="post.id">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
      </div>
  </div>
</template>

<script>


export default {
  name: "app",

  computed: {
    allPosts() {
      return this.$store.getters.allPosts;
    }
  },

  data() {
    return {
      posts: []
    };
  },
  async mounted() {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts?_limit=5");
    const posts = await res.json();
    this.posts = posts;
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 800px;
}

.post {
  border: solid 1px #cccccc;
  border-radius: 10px;
  margin-bottom: 1rem;
}
</style>
