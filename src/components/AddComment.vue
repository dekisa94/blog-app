<template>
<div>
    <form @submit.prevent="submit">
          <h2>Add comment</h2>
          <div class="form-group">
                <label for="text">Comment text</label>
                <input v-model="newComment.text" 
                    type="text" 
                    id="text" 
                    name="text" 
                    class="form-control"  
                    required
                />
            </div>
                <input type="submit" class="btn btn-success" />
      </form>
</div>
</template>

<script>
import {postService} from '../service/PostService'
export default {
  data(){
      return{
          newComment: {text: ''}
      }
  },
  methods:{
      submit(){
          postService.addComment(this.newComment, this.$route.params.id)
      }
  }
}
</script>
