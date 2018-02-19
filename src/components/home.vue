<template>
  <div class="home">
    <carousel :autoplay="false" :autoplayTimeout="3000" :perPage="1">
      <slide>
        <img class="background" src="https://clarovideocdn4.clarovideo.net/SERIES/GIGANTESDEMXICO-01-01-00/EXPORTACION_WEB/CLEAN/GIGANTESDEMXICO-01-01-00_e-1280x720.jpg">
        <div class="whiteOverlay"></div>
        <img class="cover" src="https://clarovideocdn2.clarovideo.net/SERIES/GIGANTESDEMXICO-01-01-00/EXPORTACION_WEB/SS/GIGANTESDEMXICO-01-01-00WVERTICAL.jpg?size=200x300">
      </slide>
      <slide>
        Slide 2 Content
      </slide>
      <slide>
        Slide 3 Content
      </slide>
    </carousel>

    <div class="search">
      <input type="text" placeholder="buscar...">
      <i class="material-icons">search</i>
    </div>

    <div class="section">
      <div class="movie"></div>
      <div class="movie"></div>
      <div class="movie"></div>
      <div class="movie"></div>
      <div class="movie"></div>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel'
export default {
  components: {
    Carousel,
    Slide
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  name: 'Home'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .home {
    background: linear-gradient(to bottom, #ffffff, #f4f3fc);
    width: 100vw;
    min-height: 100vh;
  }

  .VueCarousel-slide .background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    min-width: 100vw;
    max-height: auto;
  }

  .VueCarousel-slide .cover {
    position: absolute;
    top: 52px;
    left: 48px;
    width: 100px;
    height: 150px;
    border-radius: 2px;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.5);
  }

  .VueCarousel-slide .whiteOverlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    height: 226px;
    background: linear-gradient(to top, #fafafd, rgba(255, 255, 255, 0.0));
    background-image: -webkit-linear-gradient(to top #fafafd 0%, rgba(255, 255, 255, 0.0));
  }

  .search {
    position: relative;
    width: calc(100vw - 32px);
    margin-left: 16px;
    height: 56px;
    border-radius: 8px;
    background: white;
    box-shadow: 0 1px 4px 0 rgba(136, 136, 136, 0.5);
    color:
  }

  .search input {
    outline: none;
    position: absolute;
    top: 0;
    left: 0;
    height: 56px;
    width: calc(100% - 12px);
    border: none;
    font-size: 18px;
    border-radius: 8px;
    padding-left: 12px;
  }

  .search i {
    position: absolute;
    top: 16px;
    right: 12px;
    color: #fc444c;
  }

  .section {
    -webkit-overflow-scrolling: touch;
    white-space: nowrap;
    margin-left: 16px;
    margin-top: 40px;
    max-width: calc(100vw - 16px);
    overflow-x: scroll;
  }

  .section .movie {
    display: inline-block;
    width: 164px;
    height: 224px;
    background-color: #d8d8d8;
    box-shadow: 0 1px 3px 0 rgba(136, 136, 136, 0.5);
  }

  @media screen and (min-width: 576px) {

  }
</style>
