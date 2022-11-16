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

            <div class="text">
              <p>Testo del Post: {{ allPosts.post_text }}</p>
            </div>

            <div class="text">
                <div v-for="(allComments, index) in allPosts.comments" :key="index">
                    <div v-if="index < 3">
                        <!-- <p>Mittente: {{ allComments.username }}</p> -->
                        <p>Commento: {{ allComments.text }}</p>
                    </div>

                    <div v-if="(index + 1) == allPosts.comments.length" class="parCommTot">
                        <p>Commenti totali: {{ allPosts.comments.length }}</p>
                    </div>
                </div> 
                
              <button @click="otherMessage(i)">Visualizza altri commenti</button>

              <div id="altriMessaggi" v-if="altriMessaggi">
                  <div v-for="(allComments, index) in posts[i].comments" :key="index">
                      <div v-if="index >= 3">
                          <p>Testo: {{ allComments.text }}</p>
                      </div>
                  </div>

                  <!-- se decommentato, al click su Visualizza altri commenti mi fa vedere i commenti di tutti i post; e non i soli commenti del post richiamato  -->
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
        // console.log(this.indexMessaggio);
        // console.log(this.posts[index].comments);
        // console.log(this.posts[index].comments[0].text);
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
    width: 500px;   
    margin: 0 auto;

    .post {
      margin-top: 30px;
      border: 1px solid grey;
      // background: red;

      .profilo {
        display: flex;
        text-align: left;
        align-items: center;
        flex-direction: row;
        justify-content: flex-start;
        padding: 20px 40px;
        // background: yellow;

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

        .parCommTot {
          margin-top: 20px;
        }
      }
    }
  }

  .spinner {
    margin-top: 100px;
    text-align: center;
  }
  
</style>