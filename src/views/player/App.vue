<template>
  <globalheader></globalheader>
  <div class="bg"></div>
    <!--<div class="div-all">
      <div class="main">
        <h1>您访问的页面正在创造中！请耐心等待！</h1>
        <n-progress
          type="line"
          :percentage="10"
          :indicator-placement="'inside'"
          processing
        />
      </div>
    </div>-->
  <div class="div-all">
    <div class="player">
      <div class="playerin" >
        <video style="width: 1180px; height: 600px;" id="video-webrtc" controls ></video>
      </div>      
      <div class="control">
        <n-input v-model:value="url" type="text" placeholder="你的播放链接"/>
        <n-button style="margin-left: 5px;" @click="play()" type="success" round>播放</n-button>
      </div>
    </div>
  </div>
</template>

<script>
import globalheader from '../../components/Header.vue'
import { ref, getCurrentInstance } from "vue";
//import gray from '../../components/Gray.vue'

export default {
  name: 'App',
  components: {
    globalheader,
    //gray
  },
  data() {
    return {
      url: '',
    }
  },
  methods: {
    play() {
      var video = document.getElementById('video-webrtc');
      var url = this.url;
      console.log(url)
      new JSWebrtc.Player(url, { video: video, autoplay: true, onPlay: (obj) => { console.log("start play") } });
    }
  }
}
</script>

<style>
body{}
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
  .player {
    margin-top: 100px;
    padding: 10px;
    
  }
  .playerin{
    position: relative;
    max-width: 1200px;
    text-align: center;
    max-height: 600px;
    margin-bottom: 5px;
  }
  .control{
    display: flex;

  }
</style>