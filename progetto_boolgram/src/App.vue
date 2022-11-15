<template>
  <div id="app">
    <NavBar />
    <div class="principal_block">
      <div class="left_block">
        <StoriesBoolgram />
        <div class="scroll">
          <PostsBoolgram />
        </div>
      </div>

      <div class="right_block">
        <ProfiliBool />
        <SuggerimentiBool />
        <FooterBool />
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';
import StoriesBoolgram from './components/ParteSinistra/StoriesBoolgram.vue';
import PostsBoolgram from './components/ParteSinistra/PostsBoolgram.vue';
import SuggerimentiBool from './components/ParteDestra/SuggerimentiBool.vue';
import ProfiliBool from './components/ParteDestra/ProfiliBool.vue';
import FooterBool from './components/ParteDestra/FooterBool.vue';

export default {
  name: 'App',
  components: {
    NavBar,
    StoriesBoolgram,
    SuggerimentiBool,
    ProfiliBool,
    FooterBool,
    PostsBoolgram
  }
}
</script>

<style lang="scss">

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

::-webkit-scrollbar {
  width: 5px;
} 

::-webkit-scrollbar-thumb {
  background: grey; 
}

#app {
  width: 100%;
  height: 100vh;

  .principal_block {
    display: flex;
    flex-direction: row;

    .left_block {
      width: 80%;

      .scroll {
        height: calc(100vh - 160px);
        background-color: lightgreen;
        overflow-y: scroll;
      }
    }

    .right_block {
      width: 20%;
    }
  }
}

</style>
