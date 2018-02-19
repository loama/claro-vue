<template>
  <div id="app">
    <div class="content">
      <router-view/>
    </div>
    <div class="navbar">
      <img src="./assets/logo.svg" class="logo">
    </div>
    <div id="bottonNav">
      <div class="nav">
        <i class="material-icons">home</i>
        <div class="detail">Inicio</div>
      </div>
      <div class="nav">
        <i class="material-icons">explore</i>
        <div class="detail">Explorar</div>
      </div>
      <div class="nav">
        <i class="material-icons"></i>
      </div>
      <div class="nav">
        <i class="material-icons">play_arrow</i>
        <div class="detail">Algo</div>
      </div>
      <div class="nav">
        <i class="material-icons">account_circle</i>
        <div class="detail">Biblioteca</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
  html, body {
    max-width: 100vw;
    max-width: 100%;
    overflow-x: hidden;
    padding: 0;
    margin: 0;
  }

  #app {
    font-family: 'Avenir-Next-Rounded-Regular';
    overflow-x: hidden;
  }

  .content {
    padding: 0;
    margin: 0;
  }

  #bottonNav {
    position: fixed;
    bottom: 0;
    left: 0;
    height: 44px;
    width: 100vw;
    background: white;
    box-shadow: 0 -1px 3px 0 rgba(136,136,136, 0.4);
  }

  .nav {
    width: calc(20vw - 4px);
    text-align: center;
    color: #9B9B9B;
    display: inline-block;
  }

  .nav i {
    margin: 4px 0 -2px 0;
  }

  .nav .detail {
    margin: -6px 0 0 0;
    font-size: 12px;
  }

  @font-face {
    font-family: 'Avenir-Next-Rounded-Regular';
    font-style: normal;
    font-weight: 400;
    src: url('./assets/fonts/avenir-next-rounded-pro-regular.otf');
  }

  @font-face {
    font-family: 'Avenir-Next-Rounded-Medium';
    font-style: normal;
    font-weight: 400;
    src: url('./assets/fonts/avenir-next-rounded-pro-medium.otf');
  }

  @font-face {
    font-family: 'Material Icons';
    font-style: normal;
    font-weight: 400;
    src: url('./assets/fonts/MaterialIcons-Regular.eot'); /* For IE6-8 */
    src: local('Material Icons'),
      local('MaterialIcons-Regular'),
      url('./assets/fonts/MaterialIcons-Regular.woff2') format('woff2'),
      url('./assets/fonts/MaterialIcons-Regular.woff') format('woff'),
      url('./assets/fonts/MaterialIcons-Regular.ttf') format('truetype');
  }

  .material-icons {
    font-family: 'Material Icons';
    font-weight: normal;
    font-style: normal;
    font-size: 24px;  /* Preferred icon size */
    display: inline-block;
    line-height: 1;
    text-transform: none;
    letter-spacing: normal;
    word-wrap: normal;
    white-space: nowrap;
    direction: ltr;

    /* Support for all WebKit browsers. */
    -webkit-font-smoothing: antialiased;
    /* Support for Safari and Chrome. */
    text-rendering: optimizeLegibility;

    /* Support for Firefox. */
    -moz-osx-font-smoothing: grayscale;

    /* Support for IE. */
    font-feature-settings: 'liga';
  }

  .VueCarousel {
    pointer-events: none;
  }

  .VueCarousel-wrapper {
    height: 226px !important;
  }

  .VueCarousel-dot-container {
    display: none !important;
  }

  .VueCarousel-slide {
    position: relative;
  }

  ::-webkit-input-placeholder { /* Chrome/Opera/Safari */
    color: #9b9b9b;
  }
  ::-moz-placeholder { /* Firefox 19+ */
    color: #9b9b9b;
  }
  :-ms-input-placeholder { /* IE 10+ */
    color: #9b9b9b;
  }
  :-moz-placeholder { /* Firefox 18- */
    color: #9b9b9b;
  }

  input {
    -moz-box-sizing: content-box;
    -webkit-box-sizing: content-box;
    box-sizing: content-box;
  }

  @media screen and (min-width: 576px) {
    .VueCarousel-wrapper {
      height: 413px !important;
    }

    #bottonNav {
      display: none;
    }

    .navbar {
      display: block;
      position: fixed;
      z-index: 9000;
      top: 0;
      left: 0;
      width: 100vw;
      min-width: 100%;
      height: 48px;
      background: white;
      box-shadow: 0 1px 0 0 #e5e5e5;
    }

    .navbar .logo {
      margin: 10px 16px;
      height: 24px;
    }
  }
</style>
