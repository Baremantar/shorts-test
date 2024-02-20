<script>
import Flicking from "@egjs/vue3-flicking";
import vid1 from "../assets/video/aqua2.mp4";
import vid2 from "../assets/video/attributes.mp4";
import vid3 from "../assets/video/beach.mp4";
import vid4 from "../assets/video/children-bar.mp4";
import vid5 from "../assets/video/park.mp4";
import vid6 from "../assets/video/WI-FI.mp4";
import vid7 from "../assets/video/zoo.mp4";
import { ref } from "vue";

const flicking = ref(null);
const data = [vid1, vid2, vid3, vid4, vid5, vid6, vid7];

export default {
  components: {
    Flicking,
  },
  data() {
    return {
      data,
      flicking,
    };
  },
  methods: {
    playSlide(e) {
      const video = e.currentTarget.currentPanel.element;
      video.play();
    },
    stopSlide(e) {
      const video = e.currentTarget.currentPanel.element;
      video.pause();
    },
    triggerSlide(e) {
        const video = e.currentTarget.currentPanel.element;
        if(video.currentTime > 0 && !video.paused){
            video.pause();
        } else if (video.paused) {
            video.play()
        }
    }
  },
};
</script>

<template>
  <Flicking
    :options="{ circular: true, horizontal: false }"
    @changed="
      (e) => {
        playSlide(e);
      }
    "
    @will-change="
      (e) => {
        stopSlide(e);
      }
    "
    @ready="
      (e) => {
        playSlide(e);
      }
    "
    @select="e => {triggerSlide(e)}"
    ref="flicking"
    class="flicker-wrapper"
  >
    <video v-for="source in data" :key="source" muted>
      <source :src="source" type="video/mp4" />
    </video>
  </Flicking>
</template>

<style scoped>
.flicker-wrapper {
  display: flex;
  flex-direction: column;
  max-width: 500px;
}
video {
  max-width: 500px;
  max-height: 900px;
}
</style>
