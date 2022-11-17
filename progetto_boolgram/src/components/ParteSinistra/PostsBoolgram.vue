<template>
    <div class="page_posts" v-if="reload">
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

                      <div class="textCommento">
                        <h3>{{ allPosts.post_text }}</h3>
                      </div>

                      <div class="text">
                                <p>Commenti</p>
                                <div class="overflowComment">
                                    <div v-for="(allComments, index) in allPosts.comments" :key="index">
                                        <div v-if="index < 3">
                                              <h4>{{index + 1}}...   Nome: {{ allComments.username }}</h4>
                                              <p class="par">{{ allComments.text }}</p>
                                        </div>

                                        <div v-if="((index + 1) == allPosts.comments.length)">
                                            <h5>Commenti totali: {{ allPosts.comments.length }}</h5>
                                        </div>
                                    </div> 

                                    <button @click="otherMessage(i)">Visualizza altri commenti</button>

                                    <div id="altriMessaggi" v-if="altriMessaggi">
                                        <div v-for="(allComments, index) in posts[i].comments" :key="index">
                                            <div v-if="index >= 3">
                                                <h4>{{index + 1}}...   Nome: {{ allComments.username }}</h4>
                                                <p class="par">{{ allComments.text }}</p>
                                            </div>
                                        </div>
                                        <!-- se decommentato, al click su Visualizza altri commenti mi fa vedere i commenti di tutti i post; e non i soli commenti del post richiamato -->
                                    </div>
                                </div>
                      </div>
          </div>
    </div> 

    <div v-else class="spinner">
        <img src="../../assets/spinner.gif" alt="">
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
        altriMessaggi: false,
        indexMessaggio: 0,
        myTime : false,
        reload : false,
      }
    },

    created(){
      this.myTime = setInterval(() => this.getPosts(), 3000);
      setTimeout(() => { clearInterval(this.myTime);}, 3100);
    },

    methods : {
      getPosts(){
        axios.get(this.apiPosts)
        .then((result) => {
          this.posts = result.data;
          this.reload = true;
          console.log(this.posts);
          console.log(this.posts[0]);
        }).catch((error) => {
          console.log("Errore", error);
        })
      },

      otherMessage(index){
        this.altriMessaggi = true;
        this.indexMessaggio = index;
        console.log(this.indexMessaggio);
        console.log(this.posts[index].comments);
        console.log(this.posts[index].comments[0].text);
        // let messaggi = document.getElementById('altriMessaggi');

        for(let i = 0; i < this.posts[this.indexMessaggio].comments.length; i++){
          // console.log(this.posts[this.indexMessaggio].comments.length);
          // console.log(this.posts[this.indexMessaggio].comments[i].text);
           let paragrafo = document.createElement('p');
           paragrafo.innerHTML = this.posts[this.indexMessaggio].comments[i].text;
           console.log(paragrafo);
          // messaggi.innerHTML += paragrafo.innerHTML;

           // alternativa per stampare gli altri commenti???
        }
      }
    }
  }
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
  .page_posts {
    width: 400px;   
    margin: 0 auto;
    

    .post {
      margin-top: 40px;
      margin-bottom: 20px;
      box-shadow: 5px 5px 5px black;

      .profilo {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        padding: 20px 30px;
        background: linear-gradient(white,rgb(138, 216, 213));

        .profilo_image {
          width: 50px;
          height: 50px;
          margin-right: 20px;

          img {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            box-shadow: 2px 2px 2px blue;
          }
        }
      }
      .post_image {
        width: 100%;
        height: 400px;

        img {
          width: 100%;
          height: 400px;
        }
      }

      .textCommento {
        padding: 20px;
        text-align: center;
        background: linear-gradient(white,rgb(138, 216, 213));
      }

      .text {
        background: linear-gradient(white,rgb(172, 167, 167));

        p {
          font-family: Verdana, Geneva, Tahoma, sans-serif;
          padding: 10px;
          font-size: 12px;
        }

        .overflowComment {
          height: 100px;
          overflow-y: scroll;

          h4 {
            margin-left: 10px;
            font-size: 15px;
          }
          
          .par {
            margin-bottom: 15px;
            margin-left: 25px;
            margin-top: -5px;
            font-size: 12px;
            color: rgb(118, 115, 115);
          }

          h5 {
            color: rgb(110, 106, 106);
            padding-left: 10px;
          }

          button {
            margin-top: 10px;
            margin-left: 10px;
            margin-bottom: 10px;
            background: linear-gradient(white,rgb(172, 167, 167));
          }
          
        }

      }
    }
  }

  .spinner {
    display: flex;
    align-items: center;
    
    img {
      width: 70px; 
      margin-left: 600px; 
      margin-top: 230px;   
    }
  }
  
</style>