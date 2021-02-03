<template>
  <div>
    <b-navbar toggleable="lg" type="dark" class="c-navbar pt-1 pb-0">
      <b-navbar-brand href="#" class="mx-auto font-weight-bold c-navbar-brand">
        Content Calendar
      </b-navbar-brand>
    </b-navbar>

    <b-navbar type="dark" class="c-navbar p-0">
      <!-- <b-navbar-toggle target="nav-collapse"></b-navbar-toggle> -->
      <div class="container-fluid">
        <b-navbar-nav>
          <b-nav-text class="px-3 c-nav-text">
            <b-icon icon="blockquote-right" class="c-icon"></b-icon>
          </b-nav-text>
        </b-navbar-nav>
        <!-- <b-collapse id="nav-collapse" is-nav> -->
        <b-navbar-nav class="mr-auto c-tabs">
          <b-nav-text
            class="c-tab is-tab-active rounded-top mr-2 d-flex align-items-center"
          >
            Campaigns
          </b-nav-text>
          <b-nav-text class="c-tab rounded-top mr-2 d-flex align-items-center">
            Team
          </b-nav-text>
        </b-navbar-nav>
        <!-- </b-collapse> -->
        <b-navbar-nav :class="{ 'c-right-content': show }">
          <b-nav-text class="c-nav-text px-3" @click="show = true">
            <b-icon icon="card-list" class="c-icon"></b-icon>
            <span class="c-text">APPS</span>
          </b-nav-text>
          <b-nav-text
            class="c-nav-text px-3"
            v-if="show"
            @click="OpenFullScreen()"
          >
            <b-icon icon="arrow-left-short" class="c-icon"></b-icon>
          </b-nav-text>
          <b-nav-text
            class="c-nav-text px-3"
            v-if="minimize"
            @click="minimizeDrawer()"
          >
            <b-icon icon="arrow-right-short" class="c-icon"></b-icon>
          </b-nav-text>
          <b-nav-text
            class="c-nav-text px-3"
            v-if="show || fullScreen"
            @click="closeDrawer()"
          >
            <b-icon icon="x-circle" class="c-icon"></b-icon>
          </b-nav-text>
        </b-navbar-nav>
      </div>
    </b-navbar>
    <div
      class="c-drawer"
      :class="{ 'c-drawer-open': show, 'c-drawer-fullscreen': fullScreen }"
    >
      <div class="content bg-white">
        <div class="container py-3">
          <h4 class="text-center text-info">Drawer Content</h4>
        </div>
      </div>
    </div>
    <div
      class="main-content bg-white"
      :class="{
        'main-content-open': show,
        'main-content-fullscreen': fullScreen,
      }"
    >
      <div class="container py-4">
        <h4 class="text-center text-primary">Tab Content</h4>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      show: false,
      fullScreen: false,
      minimize: false,
    };
  },
  methods: {
    OpenFullScreen: function () {
      this.show = false;
      this.fullScreen = true;
      this.minimize = true;
    },
    closeDrawer: function () {
      this.show = false;
      this.fullScreen = false;
      this.minimize = false;
    },
    minimizeDrawer: function () {
      this.show = true;
      this.fullScreen = false;
      this.minimize = false;
    },
  },
};
</script>

<style lang="scss">
.c-navbar {
  background-color: #1283da;

  .c-text {
    color: white;
    font-size: 1rem;
    padding-left: 4px;
    font-weight: 500;
  }
  .c-icon {
    color: white;
    font-size: 1.4rem;
  }
  .c-navbar-brand {
    letter-spacing: 2px;
  }
  .c-nav-text {
    cursor: pointer;
  }
  .c-right-content {
    width: 25%;
    color: red;
  }
  .c-tabs {
    position: absolute;
    display: flex;
    height: 100%;
    left: 8%;
  }
}

.c-tabs .c-tab {
  padding-left: 30px;
  padding-right: 30px;
  background-color: rgb(17, 37, 149);
  color: white;
  letter-spacing: 1px;
  margin-right: 20px;
  padding-top: 0;
  padding-bottom: 0;
}
.c-tabs .is-tab-active {
  color: black;
  background-color: white;
}
/* right drawer */
.c-drawer {
  position: fixed;
  width: 0%;
  height: 100%;
  background-color: #1283da;
  right: 0;
  transition: 0.5s;
  .content {
    width: 100%;
    height: 100%;
    margin-left: 10px;
    background-color: white;
  }
}
.c-drawer-open {
  width: 25%;
  transition: 0.5s;
}

.c-drawer-fullscreen {
  width: 100%;
  transition: 0.5s;
}
/* tab content */
.main-content {
  width: 100%;
  height: calc(100vh - 88px);
  background-color: white;
  transition: 0.5s;
}
.main-content-open {
  width: 75%;
  transition: 0.5s;
}
.main-content-fullscreen {
  width: 0%;
  transition: 0.5s;
}

@media only screen and (max-width: 480px) {
  .c-drawer-open {
    width: 85%;
    transition: 0.5s;
  }
}

@media only screen and (min-width: 480px) and (max-width: 768px) {
  .c-drawer-open {
    width: 60%;
    transition: 0.5s;
  }
}

@media only screen and (min-width: 768px) and (max-width: 1024px) {
}
</style>