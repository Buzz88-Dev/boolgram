<template>
  <div class="navbar">
    <div class="image">
      <img alt="Vue logo" src="../assets/logo.png">
    </div>
    <input type="text" placeholder="Search...">
    <div class="icone">
      <font-awesome-icon icon="fa-solid fa-star" />
      <i class="fas fa-ellipsis-v single_icon"></i>
      <i class="fas fa-bell-slash"></i>
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
  color: white;
  height: 80px;
  padding: 10px 100px;
  display: flex;
  justify-content: space-between;
  flex-direction: row;
  align-items: center;

  .image {
    height: 50px;

    img {
      height: 50px;
    }
  }

  .icone {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    color: black;

    .single_icon {
      margin: 0 20px;
    }
  }
}

</style>
