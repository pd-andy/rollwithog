<template>
  <main class="container">
    <div class="header-image">
      <img src="/img/title.png">
    </div>
    <split-container class="video-player"/>
    <div class="social-media">
      <img src="/img/ig.png">
      <img src="/img/fb.png">
      <img src="/img/twitter.png">
      <img src="/img/apple.png">
      <img src="/img/spotify.png">
    </div>
  </main>
</template>

<script>
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

    }
  },
  computed: {},
  // when component uses other components
  components: {
    SplitContainer
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

  .social-media > img {
    width: 24px;
    height: 24px;
  }
</style>