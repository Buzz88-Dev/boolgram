<template>
    <div class="page_posts">
        <div v-for="(allPosts, i) in posts" :key="i" class="post">
          <div class="profilo">
            <div class="profilo_image">
              <img :src="allPosts.profile_picture">
            </div>  
            <p>{{allPosts.profile_fullname}} </p>
          </div>

          <div class="post_image">
              <img :src="allPosts.post_image">
          </div> 
          <div class="text">
            <p>{{ allPosts.post_text }}</p>
          </div>
          <div class="text">
            <p>Commenti:</p>
            <div v-for="(allComments, index) in allPosts.comments" :key="index">
              <div v-if="index < 3">
                <!-- <p>Mittente: {{ allComments.username }}</p> -->
                <p>Testo: {{ allComments.text }}</p>
              </div>
            </div>
            <p>Commenti totali: {{ allPosts.comments.length }}</p>
          </div>
        </div>  
    </div> 
</template>
  
<script>
  import axios from "axios";

  export default {
    name: 'PostsBoolgram',

    data(){
      return {
        apiPosts : "https://flynn.boolean.careers/exercises/api/boolgram/posts",
        posts : [],
        commenti: '',
      }
    },

    created(){
      this.getPosts()
    },

    methods : {
      getPosts(){
        axios.get(this.apiPosts)
        .then((result) => {
          this.posts = result.data;
          console.log(this.posts);
        }).catch((error) => {
          console.log("Errore", error);
        })
      },
    }
  }
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
  .page_posts {
    width: 500px;
    margin: 0 auto;

    .post {
      margin-top: 30px;
      background: red;

      .profilo {
        display: flex;
        text-align: left;
        align-items: center;
        flex-direction: row;
        justify-content: flex-start;
        padding: 20px 40px;
        background: yellow;

        .profilo_image {
          width: 50px;
          height: 50px;
          margin-right: 20px;

          img {
            width: 50px;
            height: 50px;
            border-radius: 50%;
          }
        }
      }
      .post_image {
        width: 100%;

        img {
          width: 100%;
        }
      }

      .text {
        padding: 20px;
      }
    }
  }
  
</style>