<template>
    <div>
      <div id="player"></div>
      <h3>正在播放：泰坦尼克号</h3>
    </div>
  </template>
  
  <script setup>
  import {defineProps, onMounted, watch} from 'vue'
  import xgplayer from 'xgplayer';
  import HlsJsPlugin from 'xgplayer-hls.js'
  
  import 'xgplayer/dist/index.min.css';
  
  const props = defineProps(["data"])
  onMounted(() => {
    play_video()
  })
  
  function play_video() {
    // const play_item = props.data.files[0]
    new xgplayer({
      id: 'player',
    //   url: play_item.url,
    //   plugins: play_item.type === "m3u8" ? [HlsJsPlugin] : [],
    //   height: "80vh",
      width: "100%",
    //   autoplay: true,
    //   poster: props.data.cover,
    });
  }
  
//   watch(
//       () => props.data.title,
//       (newValue, oldValue) => {
//         play_video()
//       }
//   )
  </script>
  <style scoped>
  </style>