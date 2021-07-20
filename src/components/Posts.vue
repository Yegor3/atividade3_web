<template>  
  <div >
  <button @click="fetchPosts" class="btn btn-success">Posts</button><br>

<ul>

<div v-for="post in posts" :key="post.id">
    <div>
      <li class="table table-dark">
         <th scope="col">Title: </th> 
         <th scope="col">Body: </th>    
        <tr>
        <th scope="col">{{post.title}}</th>
        <th scope="col">{{post.body}}</th>
        </tr>
    </li>
</div>
</div>
</ul>
</div>
</template>
<script>
export default {
    name: "Posts",
    data() {
    return {
     posts: [],
     baseURI: "https://jsonplaceholder.typicode.com/posts"
    };
    },
    methods: {
    fetchPosts: function() {
      this.$http.get(this.baseURI).then((result) => {
      this.posts = result.data;
    });
    },
    },
};
</script>