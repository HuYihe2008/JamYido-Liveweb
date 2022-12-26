<template>
    <div class="header">
        
        <ul class="jamyido-head-left">
            <img src="../assets/logo.png" width="40px" height="40px" style="margin-right: 10px;">
            <li class="jamyido-head-li">
                <a href="//www.jamyido.top" target="_blank">
                    <span>主站</span>
                </a>
            </li>
            <li class="jamyido-head-li">
                <a href="./" target="_blank">
                    <span>直播</span>
                </a>
            </li>
            <li class="jamyido-head-li">
                <a href="./player.html" target="_blank">
                    <span>WebRTC播放器</span>
                </a>
            </li>
            <li class="jamyido-head-li">
                <a href="./all.html" target="_blank">
                    <span>全部</span>             
                </a>
            </li>
        </ul>
        <div class="search"></div>
        <ul class="jamyido-head-right">
            <n-avatar round :size="30" src="https://07akioni.oss-cn-beijing.aliyuncs.com/07akioni.jpeg"/>
            <a href="./user.html" target="_blank"><n-button color="#4ea8ef" class="right-button">用户中心</n-button></a>
        </ul>
    </div>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
    color: black;
}
.header{
    position: fixed;
    top: 0;
    z-index: 1002;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 24px;
    max-width: 2560px;
    width: 100%;
    height: 64px;
    background-color: aliceblue;
}

.jamyido-head-left{
    display: flex;
    align-items: center;
    flex-shrink: 0;
    list-style-type: none;
    text-align: center  ;
    width: 400px;
}
.jamyido-head-li{
    width: 50px;
    margin-top: 0px;
    transition-duration: 300ms;
}
.jamyido-head-li:hover {
    margin-top:-10px;
    transition-duration: 300ms;
}
.search{
    width: 400px;
}
.jamyido-head-right{
    display: flex;
    align-items: center;
    margin-left: 50px;
    width: 400px;
}
.right-button{
    left: 20px;
}
</style>