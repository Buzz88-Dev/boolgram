<template>
   <div class="story_sugg">
      <div class="paragrafo">
        <p>Suggerimenti per te</p>
        <p>Mostra tutti</p>
      </div>
      <div class="suggerimenti">
          <div v-for="(allStories) in stories" :key="allStories.index" class="container_sugg">
            <div class="image">
                <img :src="allStories.profile_picture">
            </div>  
            <p>{{allStories.profile_name}}</p>        
          </div>
    </div>    
   </div>
</template>
  
<script>
  import axios from "axios";

  export default {
      name: 'SuggerimentiBool',

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
            console.log(this.stories);
          }).catch((error) => {
            console.log("Errore", error);
          })
        },
      }
  }
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
  .story_sugg {
    height: calc(100vh - 160px);     
    overflow-y: scroll;
    .paragrafo {
    font-size: 10px;
    display: flex;
    text-align: center;
    justify-content: space-between;
    flex-direction: row;
    margin: 10px 0px;
    background: orange;
  }
  .suggerimenti {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: left;
    margin: 20px;
    background: orange;

    .container_sugg {
      display: flex;
      margin: 20px 0px;
      align-items: center;
      background: green;

      p {
        font-size: 10px;
        margin-left: 10px;
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
  }
  
</style>
  