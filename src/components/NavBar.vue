<template>
<div>
  <div v-if="!mobile">
desktop
  </div>
  <div class="topnav" v-else>
    <a href="#home" class="active">Logo</a>
    <!-- Navigation links (hidden by default) -->
    <div id="myLinks">
      <a href="#about">About</a>
    </div>
    <a href="javascript:void(0);" class="icon" @click="openMenu()">
      <i class="fa fa-bars"></i>
    </a>
  </div>
</div>
</template>

<script>
export default {
  name: 'NavBar',
  props: {
    msg: String
  },
  computed: {
    mobile () {
      return window.screen.width < 768
    }
  },
  methods: {
    openMenu () {
      console.log(this.mobile)
      var x = document.getElementById('myLinks')
      if (x.style.display === 'block') {
        x.style.display = 'none'
      } else {
        x.style.display = 'block'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.topnav {
  overflow: hidden;
  background-color: #333;
  position: relative;
}

/* Hide the links inside the navigation menu (except for logo/home) */
.topnav #myLinks {
  display: none;
}

/* Style navigation menu links */
.topnav a {
  color: white;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
  display: block;
}

/* Style the hamburger menu */
.topnav a.icon {
  background: black;
  display: block;
  position: absolute;
  right: 0;
  top: 0;
}

/* Add a grey background color on mouse-over */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}

/* Style the active link (or home/logo) */
.active {
  background-color: #4caf50;
  color: white;
}
</style>
