<template>
  <div>
    <b-navbar toggleable="lg" type="dark" class="c-navbar pt-1 pb-0">
      <b-navbar-brand href="#" class="mx-auto font-weight-bold c-navbar-brand">
        Content Calendar
      </b-navbar-brand>
    </b-navbar>
    <b-navbar toggleable="lg" type="dark" class="c-navbar p-0">
      <div class="container-fluid">
        <b-navbar-nav>
          <b-nav-text class="px-3 c-nav-text">
            <b-icon icon="blockquote-right" class="c-icon"></b-icon>
          </b-nav-text>
        </b-navbar-nav>
        <b-navbar-nav class="mr-auto c-tabs">
          <b-nav-text class="c-tab rounded-top mr-2 d-flex align-items-center">
            Hello
          </b-nav-text>
        </b-navbar-nav>
        <b-navbar-nav :class="{ 'c-right-content': show }">
          <b-nav-text class="c-nav-text px-3" @click="show = true">
            <b-icon icon="menu-app" class="c-icon"></b-icon>
            <span class="c-text">APPS</span>
          </b-nav-text>
          <b-nav-text
            class="c-nav-text px-3"
            v-if="show || fullScreen"
            @click="OpenFullScreen()"
          >
            <b-icon icon="arrows-fullscreen" class="c-icon"></b-icon>
          </b-nav-text>
          <b-nav-text
            class="c-nav-text px-3"
            v-if="show || fullScreen"
            @click="closeDrawer()"
          >
            <b-icon icon="x" class="c-icon"></b-icon>
          </b-nav-text>
        </b-navbar-nav>
      </div>
    </b-navbar>
    <div
      class="c-drawer"
      :class="{ 'c-drawer-open': show, 'c-drawer-fullscreen': fullScreen }"
    >
      <div class="content bg-white">ok</div>
    </div>
    <div
      class="main-content bg-white"
      :class="{
        'main-content-open': show,
        'main-content-fullscreen': fullScreen,
      }"
    ></div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      show: false,
      fullScreen: false,
    };
  },
  methods: {
    OpenFullScreen: function () {
      this.show = false;
      this.fullScreen = true;
    },
    closeDrawer: function () {
      this.show = false;
      this.fullScreen = false;
    },
  },
};
</script>

<style lang="scss">
.c-navbar {
  background-color: #1283da;
}
.c-navbar-brand {
  letter-spacing: 2px;
}
.c-nav-text {
  cursor: pointer;
}
.c-tabs {
  background-color: #1283da;
}
.c-navbar .c-icon {
  color: white;
  font-size: 1.5rem;
}
.c-navbar .c-text {
  color: white;
  font-size: 1.2rem;
  padding-left: 4px;
  font-weight: 500;
}
.c-right-content {
  width: 25%;
  // transition: 0.5s;
  color: red;
}
.c-tabs {
  position: absolute;
  display: flex;
  height: 100%;
  left: 8%;
}
.c-tabs .c-tab {
  padding-left: 30px;
  padding-right: 30px;
  background-color: white;
  color: black;
  margin-right: 20px;
  padding-top: 0;
  padding-bottom: 0;
}

.c-drawer {
  position: fixed;
  width: 0%;
  height: 100%;
  background-color: #1283da;
  right: 0;
  transition: 0.5s;
}
.c-drawer-open {
  width: 25%;
  transition: 0.5s;
}
.c-drawer-fullscreen {
  width: 100%;
  transition: 0.5s;
}
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
.c-drawer .content {
  width: 100%;
  height: 100%;
  margin-left: 10px;
  background-color: white;
}
</style>