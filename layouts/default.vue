<template>
  <div class="container">
    <nuxt/>
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

    }
  },
  computed: {},
  // when component uses other components
  components: {},
  // methods
  watch: {},
  methods: {},
  // component Lifecycle hooks
  beforeCreate () {},
  mounted () {}
}
</script>

<style>
  * {
    margin: 0;
    border: 0;
    box-sizing: border-box;
  }

  html, body {
    background-color: black;
  }
</style>