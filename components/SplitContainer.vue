<template>
  <div class="video-container" >
    <div class="ratio-16-9 top">
      <video src="vid/country720.mp4" @click="togglePlay"/>
    </div>
    <div class="16-9 bottom">
      <video src="vid/road720.mp4" muted @click="togglePlay"/>
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
      dragging: false,
      mouseX: 0,
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
    ready () { console.log(this.ready) }
  },
  methods: {
    startDrag (e) {
      this.dragging = true
    },
    stopDrag () {
      this.dragging = false
    },
    mouseMoving (e) {
      if (this.dragging) {
        this.mouseX = (e.pageX / window.innerWidth) * 100
      }
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
    }).then(() => this.ready = true)
  }
}
</script>

<style>
  .video-container {
    position: relative;
    overflow: hidden;
    width: 100vw;
  }

  .splash {
    height: 100%;
    object-fit: cover;
    object-position: center;
    width: 100vw;
  }

  .ratio-16-9 {
    padding-bottom: 56.25%;
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

  .bottom {
    z-index: 1;
  }

  .top {
    z-index: 2;
  }
</style>