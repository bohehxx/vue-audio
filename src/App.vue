<template>
  <div id="app">
    <el-button @click="show">按钮</el-button>
    
    <vue-video :videoId="'audio1'" ></vue-video>


    <vue-video :videoId="'audio2'"  ></vue-video>
  </div>
</template>

<script>
import VueVideo from "./components/video";
// import HelloWorld from "./components/HelloWorld";
export default {
  name: "App",
  components: {
    VueVideo,
    // HelloWorld
  },
  methods: {
    show() {
      this.$message("element-ui提示");
    }

  },
  mounted() {
    // 获取所有audios
   console.log(this.$refs.child,'999')
    var audios = document.getElementsByTagName("audio");

    
    function pauseAll() {
      var self = this;
      [].forEach.call(audios, function (i) {
        i !== self && i.pause();
      });
    }

    // 给play事件绑定暂停函数

    [].forEach.call(audios, function (i) {
    
      i.addEventListener("play", pauseAll.bind(i));
    });
  },
};
</script>

<style>
</style>
