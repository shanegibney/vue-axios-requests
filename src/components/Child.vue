<template lang="html">
  <div>
    <h1>I am the child component</h1>
    Search titles: <input type="text" v-model="searchTerm">
    Note: cannot do axios requests on gh-pages
    <h4> <a href="https://github.com/shanegibney/vue-axios-requests">return to repo</a> </h4>
    <div v-for="item in filteredPosts" :key="item.id">
      <h3>{{ item.title }}</h3>
      <p>{{ item.body | snippet }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Child',
  data(){
    return {
      posts: [],
      searchTerm: ''
    }
  },
  computed: {
    filteredPosts(){
      return this.posts.filter(post => {
         return post.title.match(this.searchTerm)
      })
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/posts/')
    .then(response => {
        // console.log(response)
        this.posts = response.data
    }).catch(err => {
      console.log(err)
    })
  }
}
</script>

<style lang="css">
h1, h2 {
  color: lightblue;
}
h3, p{
  text-align: left;
}
</style>
