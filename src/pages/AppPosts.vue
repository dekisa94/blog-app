<template>
  <div class="container">
      <div v-for="(post, key) in posts" 
      :key="key">
      <h1>{{post.title}}</h1>
      </div> 
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
