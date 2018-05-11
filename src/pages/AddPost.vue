<template>
  <div class="container">
      <form @submit.prevent="submit" @reset="reset()">
          <h2>{{ this.$route.params.id ? 'Edit post' : 'Add new post'}}</h2>
          <div class="form-group">
                <label for="title">Post title</label>
                <input v-model="newPost.title" 
                    type="text" 
                    id="title" 
                    name="title" 
                    class="form-control" 
                    pattern=".{2,}"   
                    required title="2 characters minimum"
                />
            </div>
            <div class="form-group">
                <label for="text">Post text</label>
                <input v-model="newPost.text" 
                    type="text" 
                    id="text" 
                    name="text" 
                    class="form-control" 
                    pattern=".{,300}"   
                    required title="300 characters maximum"
                />
            </div>
            <div class="form-group">
                <input type="submit" class="btn btn-success" />
                <input type="reset" class="btn btn-danger" />
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
          if(this.$route.params.id)
          {
              postService.edit(this.$route.params.id, this.newPost)
              this.$router.push('/posts')
          }else
          {
            postService.add(this.newPost)
            this.$router.push('/posts')
          }
      },
      reset(){
          this.newPost= {}
      }
  },
  created(){
      if(this.$route.params.id)
      {
        postService.get(this.$route.params.id)
        .then((response) => {
            this.newPost=response.data
        })
      }
  }
}
</script>
