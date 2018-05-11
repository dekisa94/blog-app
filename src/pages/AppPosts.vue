<template>
  <div class="container">
      <ul class="list-group" v-for="(post, key) in posts" :key="key">
        <hr>
        <li class="list-group-item"><h3>{{post.title}}</h3></li>
        <router-link class="btn btn-primary" :to="{name: 'single-post', params: {id: post.id}}">View Post</router-link>
        <hr>
      </ul>
  </div>
</template>

<script>
import {postService} from '../service/PostService'
export default {
    data(){
        return{
            posts: []
        }
    },
  created(){
      postService.getAll()
      .then((response) => {
          this.posts=response.data
      })
  }
}
</script>
