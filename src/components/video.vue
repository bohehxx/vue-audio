<template>
  <div class="hello">
    <audio src="../assets/4x.mp3" :id="videoId" controls="controls" :currentTime="currentTime"></audio>
    <div class="play"  v-if="audioPlayShow" @click="playAudio">
      播放
</div>
<!-- 暂停-->
<div class="play"  v-if="!audioPlayShow" @click="pauseAudio">
   暂停
</div>
  </div>
</template>

<script>
export default {
  name: 'Video',
  props:{
   videoId:{
       type:String,
       default:''
   }
  },
  data(){
    return {

        audioPlayShow:true,
        currentTime:0
        
    }
  },


  methods:{
     playAudio() {
      
      
            //  this.audioPlayShow = false
                let id = this.videoId
                 let audio = this.audio = document.getElementById(id)
                 console.log(this.audio.paused)
                  audio.play()

      
               

     },
       pauseAudio() {
        //    alert(2)
                // this.audioPlayShow = true
                 let id = this.videoId
                let audio = document.getElementById(id)
                audio.pause()
                
            },
            setStatusPause(){
                this.audioPlayShow = true
            }
  },
  mounted(){
       let id = this.videoId
      var audio = document.getElementById(id);
      let that = this
      audio.addEventListener("pause", function(){
        
      that.audioPlayShow = true
       
    
      
      }
      );
       audio.addEventListener("play",function(){
        audio.currentTime = 0
      that.audioPlayShow = false
       

       }
      );
        
    audio.addEventListener('ended', function () {  
 
        that.audioPlayShow = true

    }, false)
   
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
