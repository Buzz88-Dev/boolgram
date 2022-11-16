<template>
    <div class="stories" v-if="reload">
        <div v-for="(allStories) in stories" :key="allStories.index" class="container_stories">
            <p>{{allStories.profile_name}}</p>
            <div class="image">
              <img :src="allStories.profile_picture">
            </div>  
        </div>
    </div>  
    <div v-else class="spinner story_sugg2">
        <img src="../../assets/spinner.gif" alt="">
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
        myTime : false,
        reload : false,
      }
    },

    created(){
      this.myTime = setInterval(() => this.getStories(), 3000);
      setTimeout(() => { clearInterval(this.myTime);}, 3100);
    },

    methods : {
      getStories(){
        axios.get(this.apiStories)
        .then((result) => {
          this.stories = result.data;
          this.reload = true;
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
    align-items: center;
    background: linear-gradient(rgb(138, 216, 213), rgb(100, 134, 236));

    .container_stories {
      display: flex;
      align-items: center;
      flex-direction: column;
      margin-left: 45px;

      p {
        font-size: 10px;
        color: black;
        letter-spacing: 1.5px;
        font-weight: bold;
      }
      .image {
        width: 60px;
        height: 60px;

      img {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        opacity: 0.5;
      }
    }
    }
  }

  .spinner {
    display: flex;
    align-items: center;
    
    img {
      width: 50px; 
      margin-left: 500px;    
    }
  }

  .story_sugg2 {
    height: 80px;  
    background: linear-gradient(rgb(138, 216, 213), rgb(100, 134, 236));
  }
  
</style>
  