<template>
  <nav class="navbar is-white" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <router-link class="navbar-item placeholder-logo" to="/" disabled>
        <img src="@/assets/logo.png" alt="Inspopaper">
      </router-link>
      <div class="navbar-burger" :class="{'is-active':showNav}" @click="showNav = !showNav" data-target="navMenu">
        <span></span> <!--wow these are the 3 bars of the hamburger icon-->
        <span></span>
        <span></span>
      </div>
    </div>
    <div class="navbar-menu" :class="{'is-active':showNav}" id="navMenu">
      <div class="navbar-end nav-slack-button">
        <a href="https://slack.com/oauth/authorize?client_id=400168532339.400446261685&scope=commands,users:read"><img alt="Add to Slack" height="40" width="139" src="https://platform.slack-edge.com/img/add_to_slack.png" srcset="https://platform.slack-edge.com/img/add_to_slack.png 1x, https://platform.slack-edge.com/img/add_to_slack@2x.png 2x" /></a>
      </div>
      <!-- <div class="navbar-start">
        <router-link class="navbar-item" to="/home" exact-active-class="is-active">Home</router-link>
        <div class="navbar-item has-dropdown is-hoverable" @mouseover="showTopDropdown = true" @mouseout="showTopDropdown = false">
          <router-link class="navbar-link" to="/about" :class="{'is-active': inAbout }">About</router-link>
          <div class="navbar-dropdown">
            <router-link class="navbar-item" to="/about">One</router-link>
            <router-link class="navbar-item" to="/about">Two</router-link>
            <router-link class="navbar-item" to="/about">Three</router-link>
            <router-link class="navbar-item" to="/about">Four</router-link>
          </div>
        </div>
      </div> -->
      
    </div>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
  data() {
    return {
      showNav: false,
      appName: process.env.VUE_APP_TITLE
    };
  },
  computed: {
    inAbout() {
      return this.$route.path.includes("/about");
    }
  },
  methods: {
    toggleHamburgerMenu() {
      this.showNav = !this.showNav;
    }
  }
};
</script>

<style>
.placeholder-logo span {
  /* font-style: italic; */
  font-weight: bold;
  /* text-transform: uppercase; */
}

.placeholder-logo .icon {
  margin-right: 0.5rem;
}

.nav-slack-button {
  padding: 10px 16px;
}
</style>
