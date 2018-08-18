<template lang="html">
  <div>
    <h1>I am the child component</h1>
    <h4> <a href="https://github.com/shanegibney/vue-axios-requests">return to repo</a> </h4>
    <div v-for="item in posts" :key="item.id">
      <h3>{{ item.title }}</h3>
      <p>{{ item.body }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Child',
  data(){
    return {
      posts: []
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
