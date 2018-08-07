<template>
  <div class="video-container" >
    <div class="toggle-area" @mousedown.prevent="toggleOverlay" @mouseup="toggleOverlay" @touchstart.prevent="toggleOverlay" @touchend.prevent="toggleOverlay"/>
    <div class="ratio-16-9">
      <video playsinline :class="`${overlay ? '' : 'top'}`" @click="togglePlay" poster="/img/splash.png">
        <source type="video/mp4" src="vid/country.mp4"/>
        <source type="video/webm" src="vid/country.webm"/>
        <source type="video/ogg" src="vid/country.ogv"/>
      </video>
      <video playsinline :class="`${overlay ? 'top' : ''}`" muted @click="togglePlay">
        <source type="video/mp4" src="vid/road.mp4"/>
        <source type="video/webm" src="vid/road.webm"/>
        <source type="video/ogg" src="vid/road.ogv"/>
      </video>
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
  watch: {
    ready () {
      if (this.ready) this.$emit('ready')
      console.log(this.ready)
    }
  },
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