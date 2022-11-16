<template>
    <div class="footer">
        <h5>@ 2020 INSTAGRAM FROM FACEBOOK</h5>
    </div>   
</template>
  
<script>
  export default {
    name: 'FooterBool',
  }
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  
  .footer {
    height: 80px;
    color: white;;
    // background: blue;
    background: linear-gradient( rgb(64, 90, 238), rgb(3, 11, 167));
    display: flex;
    align-items: center;
    text-align: center;

    h5 {
      font-size: 10px;
      margin-left: 20px;
      letter-spacing: 2px;
    }
  }
  
</style>