<template>
  <div class="container">
      <ul class="list-group" v-for="(post, key) in posts" :key="key">
        <hr>
        <li class="list-group-item"><h3>{{post.title}}</h3></li>
        <li class="list-group-item">
            <router-link class="btn btn-warning" :to="{name: 'edit-post', params: {id: post.id}}">Edit</router-link>
            <button class="btn btn-danger" @click="deletePost(post.id)">Delete</button>
        </li>
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
  beforeRouteEnter (to, from, next) {
    postService.getAll()
      .then((response) => {
        next((vm) => {
          vm.posts = response.data
        })
      }).catch((error) => {
        console.log(error)
      })
  },
  methods:{
      deletePost(id){
          postService.delete(id)
          this.posts = this.posts.filter(post => post.id !== id)
      }
  }
}
</script>
