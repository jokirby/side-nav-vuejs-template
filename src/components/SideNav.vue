<template>
  <div>
    <!-- <b-button v-b-toggle.sidebar-1>Toggle Sidebar</b-button> -->
    <b-sidebar visible="true" no-close-on-route-change="!mobile" no-close-on-esc="!mobile" id="sidebar-1" title="Ira Stuff" :width="navWidth">
      <div class="px-3 py-2">
        <!-- <b-img src="https://picsum.photos/500/500/?image=54" fluid thumbnail></b-img> -->
       <div id="nav">
          <router-link to="/">Portfolio</router-link> |
          <router-link to="/about">About</router-link>
        </div>
      </div>
    </b-sidebar>
  </div>
</template>

<script>
export default {
  name: 'SideNav',
  props: {},
  data () {
    return {
      windowWidth: window.screen.width
    }
  },
  computed: {
    navWidth () {
      return this.mobile ? '100%' : '320px'
    },
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
    this.$nextTick(function () {
      // Code that will run only after the
      // entire view has been rendered
      document.querySelector('.b-sidebar-header .close').style.display = 'none'
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
