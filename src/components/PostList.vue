<template>
  <div>
    <h1>Post List</h1>
    <button @click="getPosts">Show Posts</button>
    <div>
      <table class="table">
        <tr>
          <th>S.no</th>
          <th>Title</th>
        </tr>
        <tr  v-for="post in posts" :key="post.id">
          <td>{{ post.id }}</td>
          <td>{{ post.title }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
  export default {
    name:'PostList',
    data(){
      return{
        posts:[],
      }
    },
    methods:{
      getPosts(){
        axios.get('https://jsonplaceholder.typicode.com/posts')
        .then((response) => {
          this.posts = response.data
        })
      }
    }
  }
</script>

<style scoped>
button{background-color: steelblue;width: 150px;height: 60px;border-radius: 5px;border: 5px solid orchid;}
  table {
  width: 50%;
  border-collapse: collapse;
  margin: 0 auto;
}

th, td {
  padding: 8px;
  border-bottom: 1px solid #ddd;
}

thead th {
  background-color: #f2f2f2;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:hover {
  background-color: cadetblue;color: aliceblue;
}

</style>