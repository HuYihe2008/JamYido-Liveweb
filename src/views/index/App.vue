<template>
  <globalheader></globalheader>
  <div class="bg">
    </div>
    <div class="div-all">
      <div class="main">
        <h1>您访问的页面正在创造中！请耐心等待！</h1>
        <n-progress
          type="line"
          :percentage="10"
          :indicator-placement="'inside'"
          processing
        />
      </div>
    </div>
</template>

<script>
import globalheader from '../../components/Header.vue'
//import gray from '../../components/Gray.vue'

export default {
  name: 'App',
  components: {
    globalheader,
    //gray
  }
}
</script>

<style>

a {
  text-decoration: none;
}
.bg{
    width: 100%;
    height: 100%;
    position: fixed;
    filter:blur(2px);
    margin-top: -60px;
    z-index:-100;
    background: url('http://api.jamyido.top/api/pic/random.php');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
  .div-all{
    margin: 10px;
    margin-left: 90px;
    margin-right: 90px;
    max-width: 1200px;
    background-color: aliceblue;
    border-radius:10px ;
  }
  .main{
    margin-top: 100px;
    padding: 10px;
  }
</style>
