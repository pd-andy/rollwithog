<template>
  <div class="video-container" >
    <div 
      class="toggle-area"
      @mousedown.prevent="toggleOverlay"
      @mouseup="toggleOverlay"
      @touchstart.prevent="toggleOverlay"
      @touchend.prevent="toggleOverlay"/>
    <div class="ratio-16-9">
      <video 
        playsinline
        src="vid/country720.mp4" 
        :class="`${overlay ? '' : 'top'}`"
        @click="togglePlay"/>
      <video 
        playsinline
        src="vid/road720.mp4" 
        :class="`${overlay ? 'top' : ''}`"
        muted 
        @click="togglePlay"/>
    </div>
  </div>
</template>

<script>
export default {
  // Do not forget this little guy
  name: '',
  // share common functionality with component mixins
  mixins: [],
  // compose new components
  extends: {},
  // component properties/variables
  props: {},
  // variables
  data () {
    return {
      overlay: false,
      playing: false,
      ready: false,
      videos: null
    }
  },
  computed: {},
  // when component uses other components
  components: {},
  // methods
  watch: {},
  methods: {
    toggleOverlay () {
      this.overlay = !this.overlay
    },
    togglePlay () {
      if (this.ready) {
        if (!this.playing) {
          this.videos.forEach(v => v.play())
          this.playing = true
        } else {
          this.videos.forEach(v => v.pause())
          this.playing = false
        }
      }
    }
  },
  // component Lifecycle hooks
  beforeCreate () {},
  mounted () {
    const videos = this.videos = document.querySelectorAll('video')

    new Promise(resolve => {
      let loaded = 0

      videos.forEach(v => {
        v.addEventListener('loadedmetadata', function() {
          loaded++

          if (loaded === videos.length) {
            resolve()
          }
        })
      })
    }).then(() => {
      console.log('???')
      this.ready = true
    })
  }
}
</script>

<style>
  .video-container {
    position: relative;
    overflow: hidden;
    width: 100vw;
  }

  .toggle-area {
    position: absolute;
    right: 0;
    bottom: 0;
    width: 25vw;
    height: 25vw;
    z-index: 99;
  }

  .ratio-16-9 {
    padding-bottom: calc(100vw * (546 / 1280));
    height: auto;
  }

  .video-container video {
    background-color: black;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: auto;
  }

  .top {
    z-index: 2;
  }
</style>