<template>
  <div class="container">
      <form @submit.prevent="submit">
          <h2>Add new post</h2>
          <div class="form-group">
                <label for="title">Post title</label>
                <input v-model="newPost.title" type="text" id="title" name="title" class="form-control" required/>
            </div>
            <div class="form-group">
                <label for="text">Post text</label>
                <input v-model="newPost.text" type="text" id="text" name="text" class="form-control" required/>
            </div>
            <div class="form-group">
                <input type="submit" class="btn btn-success" />
            </div>
      </form>
  </div>
</template>

<script>
import {postService} from '../service/PostService'
export default {
  data(){
      return{
          newPost: {title: '', text: ''}
      }
  },
  methods:{
      submit(){
          postService.add(this.newPost)
          this.$router.push('/posts')
      }
  }
}
</script>
