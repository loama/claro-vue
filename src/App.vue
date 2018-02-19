<template>
  <div id="app">
    <div class="content">
      <router-view/>
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
    box-shadow: 0 -1px 3px 0 rgba(136,136,136, 0.5);
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
</style>
