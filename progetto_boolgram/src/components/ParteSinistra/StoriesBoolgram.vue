<template>
    <div class="stories">
        <div v-for="(allStories) in stories" :key="allStories.index" class="container_stories">
            <p>{{allStories.profile_name}}</p>
            <div class="image">
              <img :src="allStories.profile_picture">
            </div>  
        </div>
    </div>   
</template>
  
<script>
import axios from "axios";

export default {
    name: 'StoriesBoolgram',

    data(){
      return {
        apiStories : "https://flynn.boolean.careers/exercises/api/boolgram/profiles",
        stories : [],
      }
    },

    created(){
      this.getStories()
    },

    methods : {
      getStories(){
        axios.get(this.apiStories)
        .then((result) => {
          this.stories = result.data;
          // console.log(this.stories);
        }).catch((error) => {
          console.log("Errore", error);
        })
      },
    }
}
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
  .stories {
    height: 80px;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    // background: pink;
    padding: 20px;

    .container_stories {
      margin: 0px 20px;
      // background: yellow;

      p {
        font-size: 10px;
      }
      .image {
      width: 50px;
      height: 50px;

      img {
        width: 50px;
        height: 50px;
        border-radius: 50%;
      }
    }
    }
  }
  
</style>
  