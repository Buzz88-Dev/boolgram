<template>
    <div class="story_sugg" v-if="reload">
        <div class="paragrafo">
            <h4>Suggerimenti per te</h4>
            <h4>Mostra tutti</h4>
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
    <div v-else class="spinner story_sugg2">
        <img src="../../assets/spinner.gif" alt="">
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
          myTime : '',
          reload : false,
        }
      },

      created(){
        // this.getStories();
        // this.myTime = setInterval(this.getStories, 3000)
        // // console.log(this.myTime);
        // this.myTimeEnd = setTimeout(clearInterval(this.myTime), 4000);

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
  
  .story_sugg {
    height: calc(100vh - 230px);     
    overflow-y: scroll;
    background: linear-gradient( rgb(100, 134, 236), rgb(64, 90, 238));
    // background: red;
      .paragrafo {
      font-size: 13px;
      display: flex;
      text-align: center;
      justify-content: space-between;
      flex-direction: row;
      margin: 30px 20px 10px 20px;

      h4:first-child  {
        opacity: 0.5;
      }

      h4:last-child:hover  {
        color: blue;
        cursor: pointer;
        font-weight: bold;
      }
    }
  .suggerimenti {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: left;
    // background: orange;

    .container_sugg {
      display: flex;
      margin: 20px 20px;
      align-items: center;
      // background: green;
      border-bottom: 1px solid blue;
      border-top: 1px solid blue;
      box-shadow: 1px 1px 1px blue;

      p {
        font-size: 13px;
        margin-left: 10px;
      }
      .image {
      width: 50px;
      height: 50px;
      margin: 5px 0;
      // background: blue;

        img {
          width: 50px;
          height: 50px;
          border-radius: 50%;
          box-shadow: 2px 2px 2px blue;
        }

        img:hover {
          cursor: pointer;
        }
      }
    }
  }
  }
  .spinner {
    display: flex;
    align-items: center;
    
    img {
      width: 20%;
      margin-left: 40%;
    }
  }
  
  .story_sugg2 {
    height: calc(100vh - 230px);     
    overflow-y: scroll;
    background: linear-gradient( rgb(100, 134, 236), rgb(64, 90, 238));
  }
</style>
  