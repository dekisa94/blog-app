<template>
    <div class="container">
        <h1>{{post.title}}</h1>
        <i>{{post.createdAt | formatDate}}</i>
        <hr>
        <p>{{post.text}}</p>
        <hr>
        <add-comment @onComment="commentRefresh" />
        <h2>Comments:</h2>
        <ul class="list-group" v-for="(comment, key) in comments" :key="key">
            <li class="list-group-item">{{comment.text}}<i class="float-right">{{comment.createdAt | diffForHumans}}</i></li>
        </ul>
    </div>
</template>

<script>
import {postService} from '../service/PostService'
import AddComment from '../components/AddComment.vue'
import { DateMixin } from '../Mixins'
export default {
    mixins: [ DateMixin ],

    components:{
        AddComment
    },
  data(){
      return{
          post: [],
          comments: []
      }
  },
  created(){
      postService.get(this.$route.params.id)
      .then((response) => {
          this.post=response.data
          this.comments=response.data.comments

      })
  },
  methods:{
      commentRefresh(){
          postService.get(this.$route.params.id)
            .then((response) => {
            this.comments=response.data.comments
      })
      }
  }
}
</script>
