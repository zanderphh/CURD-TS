<template>
  <div id="mse"></div>
</template>

<script lang='ts'>
import { onMounted } from "vue";
import Player from "xgplayer/dist/simple_player";
import { volume, playbackRate, screenShot } from "xgplayer/dist/controls";
import { deviceDetection } from "../../../utils/deviceDetection"

export default {
  setup() {
    onMounted(() => {
      let player = new Player({
        id: "mse",
        autoplay: false,
        screenShot: true,
        url:
          "https://sf1-hscdn-tos.pstatp.com/obj/media-fe/xgplayer_doc_video/mp4/xgplayer-demo-720p.mp4",
        poster:
          "https://s2.pstatp.com/cdn/expire-1-M/byted-player-videos/1.0.0/poster.jpg",
        fluid: deviceDetection() ? true : false,
        controlPlugins: [volume, playbackRate, screenShot],
        playbackRate: [0.5, 0.75, 1, 1.5, 2], //传入倍速可选数组
      });
    });
    return {};
  },
};
</script>

<style lang="scss" scoped>
#mse {
  flex: auto;
}
</style>
