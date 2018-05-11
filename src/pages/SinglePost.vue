<template>
    <div class="container">
        <h1>{{post.title}}</h1>
        <i>{{post.createdAt}}</i>
        <hr>
        <p>{{post.text}}</p>
    </div>
</template>

<script>
import {postService} from '../service/PostService'
export default {
  data(){
      return{
          post: []
      }
  },
  created(){
      postService.get(this.$route.params.id)
      .then((response) => {
          this.post=response.data
      })
  }
}
</script>
