<template>
    <n-message-provider>
      <MessageApi />
    </n-message-provider>
    <div class="bg">
    </div>
    <globalheader></globalheader>
  <div class="div-all">
    <div class="user-head">
      <h1>欢迎来到直播用户中心</h1>
      <p>尊敬的用户，以下我们将免费为您提供直播串流服务，请您查看您的推流密钥与推流地址，注意播放地址！</p>
    </div>
  </div>
  <div class="div-all">
    <div class="informaintion">
      <h2>串流地址</h2>
      <ul class="">
        <li>
          <span>WebRTC超低延迟  </span><br>
          <n-input v-model:value="livewebfast" type="text" readonly placeholder=""/>
            <!--input value='' type="text" readonly="" id="input1"-->
        </li>
        <li>
          <span>超低延迟  </span><br>
          <n-input v-model:value="liveweb1" type="text" readonly placeholder=""/>
            <!--input value='' type="text" readonly="" id="input1"-->
        </li>
        <li>
          <span>低延迟  </span><br>
          <n-input v-model:value="liveweb2" type="text" readonly placeholder=""/>
            <!--input value='' type="text" readonly="" id="input2"-->
        </li>
        <li>
          <span>正常 </span><br>
          <n-input v-model:value="liveweb3" type="text" readonly placeholder=""/>
            <!--input value='' type="text" readonly="" id="input3"-->
        </li>
        <n-button @click="getlink = true" type="success" round style="margin-top: 5px;">获取直播服务链接</n-button>
        <n-modal
          v-model:show="getlink"
          :mask-closable="false"
          preset="dialog"
          title="是否同意本协议"
          positive-text="同意"
          negative-text="再想想"
          @positive-click="onGetlinkTrue"
          @negative-click="onGetlinkFalse"
        >
        <n-card
          title="点击同意即代表您同意使用以下协议"
        ><a href="#">《JamYido社区用户使用条例》</a><br><a href="#">《JamYido直播服务协议》</a></n-card>
      </n-modal>
      </ul>
      <h2>直播密钥</h2>
      <ul>
        <li>
          <span>请在下方输入您的JamYido社区账户ID</span><span>   注册链接: <a href='https://www.jamyido.top/user-sign/' >{{ reg }}</a></span><br>
          <!--input value="" type="number" id="inputid"-->
          <n-input-number id="inputid"  v-model:value="id" clearable placeholder="请输入您的ID" style="margin-bottom: 5px;" />
          <n-button @click="getkey = true" type="success" round>获取密钥</n-button>
          <n-modal
          v-model:show="getkey"
          :mask-closable="false"
          preset="dialog"
          title="我们需要再次确认"
          positive-text="同意"
          negative-text="再想想"
          @positive-click="onGetKeyTrue"
          @negative-click="onGetKeyFalse"
        >
        <n-card
          title="点击同意即代表您同意使用以下协议"
        ><a href="#">《JamYido社区用户使用条例》</a><br><a href="#">《JamYido直播服务协议》</a></n-card>
      </n-modal>
          <br>
        </li>
        <li>
          <span>您的密钥：</span>
          <!--input value='' type="text" readonly="" id="input4"-->
          <n-input v-model:value="key" type="text" readonly placeholder=""/>
        </li>
      </ul>

    </div>
  </div>
  <div class="div-all">
    <div class="play">
      <h2>播放链接</h2>
      <ul>
        <li>
          <span>WebRTC超低延迟播放链接</span>
          <n-input v-model:value="playfast" type="text" readonly placeholder=""/>
        </li>
        <li>
          <span>超低延迟播放链接</span>
          <n-input v-model:value="play1" type="text" readonly placeholder=""/>
        </li>
        <li>
          <span>低延迟播放链接</span>
          <n-input v-model:value="play2" type="text" readonly placeholder=""/>
        </li>
        <li>
          <span>正常延迟播放链接</span>
          <n-input v-model:value="play3" type="text" readonly placeholder=""/>
        </li>
      </ul>
    </div>
  </div>
</template>
  
  <script>
import MessageApi from "./assets/content.vue";  
import globalheader from '../../components/Header.vue'
import { ref, getCurrentInstance } from "vue";
import { before } from "lodash";
  //import gray from '../../components/Gray.vue'

  

  export default {
    name: 'App',
    components: {
      globalheader,MessageApi
      //gray
    },
    data() {
      return {
        liveweb1:'',
        liveweb2:'',
        liveweb3:'',
        livewebfast:'',
        key:'',
        id: ref(),
        play1:'',
        paly2:'',
        paly3:'',
        playfast:'',
        reg: 'https://www.jamyido.top/user-sign/'
      }
    },
   
    setup(){
      const getlinkRef = ref(false);
      const getkeyRef = ref(false);
      const { proxy } = getCurrentInstance()
        return { 
        //授权提示框开始
        getlink: getlinkRef,
        onGetlinkTrue() {
          window.$message.success("感谢您使用JamYido直播服务");
          getlinkRef.value = false;
          proxy.$data.liveweb1 = 'rtmp://flv.rtmp.live.jamyido.top/live/',
          proxy.$data.liveweb2 = 'rtmp://hls.rtmp.live.jamyido.top/live/',
          proxy.$data.liveweb3 = 'rtmp://rtmp.live.jamyido.top/live/',
          proxy.$data.livewebfast = 'rtmp://webrtc.rtmp.live.jamyido.top/live/'
        },
        onGetlinkFalse() {
          window.$message.error("抱歉您拒绝了服务条款")
          getlinkRef.value = false;
        },



        getkey: getkeyRef,
        onGetKeyTrue() {
          window.$message.success("感谢您使用JamYido直播服务");
          getkeyRef.value = false;
          proxy.getid();
          proxy.play();
        },
        onGetKeyFalse() {
          window.$message.error("抱歉您拒绝了服务条款")
          getkeyRef.value = false;
        }
        //授权提示框结束
      }
    },
    mounted() {

    },
    methods: {
      getid () {
        var id = this.id;
        this.axios.get("https://www.jamyido.top/author/" + id + '/')
        .then((response) =>{
          const axios = require('axios');
          console.log(response.status);
          var result = (response.status);
          if ( result = "200" ) {
            console.log("成功")
            window.$message.success('验证成功')
            //密钥同步验证
            axios.post("https://background.live.jamyido.top/terraform/v1/mgmt/secret/token",
            {
              "apiSecret": "srs-v1-51d04f9cdf6840709cb87d6c70510b4d"
            }).then((response) =>
            {
              console.log(response.data.data.token);
              var token = response.data.data.token
              const axios = require('axios');
              axios.post("https://background.live.jamyido.top/terraform/v1/hooks/srs/secret/query",{
                "token": token
              },).then((response)=>{
                console.log(response.data.data.publish)
                var publish = response.data.data.publish
                this.key = id + '?' + 'secret=' + publish
                //document.getElementById("input4").value = id + '?' + publish
              })
            })
          } 
        })
        .catch(function (error) {
          if (error.response) {
      // 请求已发出，但服务器响应的状态码不在 2xx 范围内
            console.log(error.response.status);
            window.$message.error('验证失败')
          } else {
      // Something happened in setting up the request that triggered an Error
            console.log('Error', error.message);
            window.$message.error('验证失败')
          }
        });
      },
      liveweb() {
        
        
      },
      play() {
        var playweb = 'https://play.live.jamyido.top/live/'
        var id = this.id
        this.playfast = 'webrtc://' + 'play.live.jamyido.top:443/live/' + id
        this.play1 = playweb + id + '.flv'
        this.play2 = playweb + id + '.flv'
        this.play3 = playweb + id + '.m3u8'
      }
    }
  }
  </script>
  
  <style>
  h1{
    font-size: 40px;
  }
  h2{
    font-size: 20px;
  }
  input{
    /*margin-bottom: 5px;*/
    width: 300px;
  }
 .bg{
    width: 100%;
    height: 100%;
    position: fixed;
    filter:blur(2px);
    z-index:-100;
    margin-top: -60px;
    background: url('http://api.jamyido.top/api/pic/random.php');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
  a {
    text-decoration: none;
  }
  .user-head{
    margin-top: 70px;
    padding: 20px;
    padding-left: 40px;
    padding-top: 1px;
  }
  .informaintion{
    padding: 20px;
    padding-left: 40px;
  }
  .div-all{
    margin: 10px;
    margin-left: 90px;
    margin-right: 90px;
    max-width: 1200px;
    background-color: aliceblue;
    border-radius:10px ;
  }
  .play{
    padding: 20px;
    padding-left: 40px;
  }
  </style>