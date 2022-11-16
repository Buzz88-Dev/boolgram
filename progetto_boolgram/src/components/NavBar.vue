<template>
  <div class="navbar">
    <div class="image">
      <img alt="Vue logo" src="../assets/logo.png">
    </div>

    <div class="input">
      <input type="text" placeholder="Search...">
    </div>

    <div class="icone">
      <div class="icona">
        <i class="fas fa-star"></i>
      </div>
      <div>
        <i class="fas fa-ellipsis-v single_icon"></i>
      </div>
      <div class="image2">
        <img src="../assets/profile.jpg" alt="">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.navbar {
  height: 80px;
  display: flex;
  justify-content: space-between;
  flex-direction: row;
  align-items: center;
  background: linear-gradient(white,rgb(138, 216, 213));

  .image {
    height: 80px;
    display: flex;
    align-items: center;
    margin-left: 100px;
    // border: 1px solid black;

    img {
      height: 50px;
    }
  }

  .input {
    height: 80px;
    display: flex;
    align-items: center;
    // border: 1px solid black;

    input {
      border: 1px solid grey;
      padding: 5px;
      background: linear-gradient(white,rgb(159, 225, 222));
      box-shadow: 5px 5px 5px black;
    }
  }

  .icone {
    height: 80px;
    display: flex;
    align-items: center;
    margin-right: 100px;
    // border: 1px solid black;

    .icona {
      display: flex;
      align-items: center;
      text-align: center;
    }
    .image2 {
      height: 40px;
      width: 40px;
      display: flex;
      align-items: center;

      img {
        width: 100%;
        height: auto;
        border-radius: 50%;
      }
    }

    .single_icon {
      margin: 0 20px;
    }
  }
}

</style>
