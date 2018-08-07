<template>
  <main class="container">
    <div class="header-image">
      <img src="img/title.png">
    </div>
    <div class="video-player">
      <split-container/>
    </div>
    <div class="social-media">
      <a href="https://www.instagram.com/danieltripleog" target="_blank">
        <img src="img/ig.png">
      </a>
      <a href="https://www.facebook.com/DanielTripleOG" target="_blank">
        <img src="img/fb.png">
      </a>
      <a href="https://twitter.com/danieltripleog" target="_blank">
        <img src="img/twitter.png">
      </a>
      <a href="https://itunes.apple.com/gb/album/roll-the-dice/1406356303?i=1406356306&app=music&ign-mpt=uo%3D4" target="_blank">
        <img src="img/apple.png">
      </a>
      <a href="https://open.spotify.com/track/5KK5eenMy6rVPEEFJAOH1F" target="_blank">
        <img src="img/spotify.png">
      </a>
    </div>
  </main>
</template>

<script>
import Loader from '~/components/Loader'
import SplitContainer from '~/components/SplitContainer'

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
      loading: true
    }
  },
  computed: {},
  // when component uses other components
  components: {
    SplitContainer,
    Loader
  },
  // methods
  watch: {},
  methods: {},
  // component Lifecycle hooks
  beforeCreate () {},
  mounted () {}
}
</script>

<style>
  .container {
    width: 100vw;
  }

  .header-image {
    width: 100%;
  }

  .loading-spinner {
    position: absolute;
    margin: auto;
    left: calc(50% - 55px);
    height: 100px;
    z-index: 99;
  }

  .video-player {
    margin: 50px 0;
  }

  .header-image > img {
    padding-top: 5%;
    padding-left: 10%;
    padding-right: 10%;
    width: 100%;
    object-fit: cover;
  }

  .social-media {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    padding: 20px 10%;
    width: 100%;
  }

  .social-media img {
    width: 24px;
    height: 24px;
  }
</style>