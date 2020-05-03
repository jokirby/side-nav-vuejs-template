<template>
  <div id="app">
    <SideNav :mobile="mobile"/>
    <router-view/>
  </div>
</template>

<script>
import SideNav from '@/components/SideNav'
export default {
  name: 'App',
  components: {
    SideNav
  },
  mixins: [],
  data () {
    return {
      windowWidth: window.screen.width
    }
  },
  computed: {
    mobile () {
      return this.windowWidth < 768
    }
  },
  methods: {
    addWindowEventListener () {
      window.addEventListener('resize', (e) => {
        this.windowWidth = e.target.screen.width
      })
    }
  },
  mounted () {
    this.addWindowEventListener()
  },
  watch: {}
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
