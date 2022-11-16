<template>
    <div class="profili" >
        <div class="image">
          <img src="../../assets/profile.jpg" alt="">
        </div>

        <div class="nomeProfilo">
          <h5>michelepapagni</h5>
          <p>Michele Papagni</p>
        </div>

        <div class="passaA">
          <p>Passa a</p>
        </div>
    </div>   
</template>
  
<script>
  export default {
    name: 'ProfiliBool',
  }
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
  .profili {
    height: 70px;
    background: linear-gradient(rgb(138, 216, 213), rgb(100, 134, 236));
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    align-items: center;

    .image {
      width: 60px;
      height: 60px;

      img {
        width: 100%;
        height: auto;
        border-radius: 50%;
      }
    };

    .nomeProfilo {
      width: 70px;
      height: 70px;
      display: flex;
      justify-content: center;
      flex-direction: column;
      align-items: center;

      h5 {
        font-size: 13px;
      }

      p {
        font-size: 10px;
        opacity: 0.5;
        margin-top: 5px;
      }
    }

    .passaA {
      display: flex;
      align-items: center;
      width: 70px;
      height: 70px;

      p {
        font-size: 15px;
      }

      p:hover {
        color: blue;
        cursor: pointer;
        font-weight: bold;
      }
    }
  }
  
</style>