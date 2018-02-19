<template>
  <div class="home">

    <div class="background"
         v-for="slide in slider.items"
         v-bind:class="{ 'active': isCurrentPage(slide.id) }"
         v-bind:style="{ backgroundImage: 'url(' + slide.image_background + ')' }"
         v-bind:key="slide.id">
    </div>

    <div class="whiteOverlay"></div>

    <carousel :autoplay="true" :autoplayTimeout="5000" :perPage="1" :loop="true" v-on:pageChange="pageChange">
      <slide v-for="slide in slider.items" v-bind:key="slide.group_id">
        <div style="margin-top:80px"> {{slide.title}} </div>
        <img class="cover" :src="slide.image_medium">
      </slide>
    </carousel>

    <div class="search">
      <input type="text" placeholder="buscar...">
      <i class="material-icons">search</i>
    </div>

    <div class="section">
      <div class="title">Claro video te recomienda</div>
      <div class="movie" v-for="movie in recommends"></div>
    </div>

    <div class="section" v-for="section in sections">
      <div class="title">{{section.title}}</div>
      <div class="movie" v-for="movie in section.content">
        <img src="">
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import { Carousel, Slide } from 'vue-carousel'
export default {
  components: {
    Carousel,
    Slide
  },
  data () {
    return {
      slider: {
        items: [],
        length: 0,
        current: 0
      },
      recommends: [],
      sections: []
    }
  },
  methods: {
    isCurrentPage (n) {
      return this.slider.current === n
    },
    pageChange () {
      // console.log(this.slider.length)
      // console.log(this.slider.current)
      var current = this.slider.current
      if (this.slider.current <= this.slider.length) {
        console.log('normal')
        this.slider.current = current + 1
      } else {
        console.log('ends')
        this.slider.current = 0
      }
      this.slider.current_id = this.slider.items[current].id
    }
  },
  mounted () {
    var self = this
    var sliderUrl = 'https://mfwkweb-api.clarovideo.net//services/cms/superhighlight?superhighlight=homeuser&region=mexico&api_version=v5.8&authpn=webclient&authpt=tfg1h3j4k6fd7&format=json&region=mexico&device_id=web&device_category=web&device_model=web&device_type=web&device_manufacturer=generic&user_status=anonymous'
    var recommends = 'https://mfwkweb-api.clarovideo.net//services/content/list?quantity=50&order_way=ASC&order_id=50&level_id=GPS&from=0&filter_id=21722&region=mexico&api_version=v5.8&authpn=webclient&authpt=tfg1h3j4k6fd7&format=json&region=mexico&device_id=web&device_category=web&device_model=web&device_type=web&device_manufacturer=generic'
    var olympic = 'https://mfwkweb-api.clarovideo.net//services/content/list?quantity=50&order_way=ASC&order_id=50&from=0&filter_id=32570&level_id=GPS&region=mexico&api_version=v5.8&authpn=webclient&authpt=tfg1h3j4k6fd7&format=json&region=mexico&device_id=web&device_category=web&device_model=web&device_type=web&device_manufacturer=generic'
    var bestSeries = 'https://mfwkweb-api.clarovideo.net//services/content/list?quantity=50&order_way=ASC&order_id=50&level_id=GPS&from=0&filter_id=16151&region=mexico&api_version=v5.8&authpn=webclient&authpt=tfg1h3j4k6fd7&format=json&region=mexico&device_id=web&device_category=web&device_model=web&device_type=web&device_manufacturer=generic'
    var rentAndSale = 'https://mfwkweb-api.clarovideo.net//services/content/list?quantity=50&order_way=ASC&order_id=50&level_id=GPS&from=0&filter_id=16088&region=mexico&api_version=v5.8&authpn=webclient&authpt=tfg1h3j4k6fd7&format=json&region=mexico&device_id=web&device_category=web&device_model=web&device_type=web&device_manufacturer=generic'
    var bestPictures = 'https://mfwkweb-api.clarovideo.net//services/content/list?quantity=50&order_way=ASC&order_id=50&from=0&filter_id=24185&level_id=GPS&region=mexico&api_version=v5.8&authpn=webclient&authpt=tfg1h3j4k6fd7&format=json&region=mexico&device_id=web&device_category=web&device_model=web&device_type=web&device_manufacturer=generic'

    axios.get(sliderUrl)
      .then(response => {
        var sliderItems = response.data.response.highlight
        for (var i = 0; i < sliderItems.length; i++) {
          var item = sliderItems[i]
          item['id'] = i
          this.slider.items.push(item)
        }
        this.slider.length = sliderItems.length
      })
      .catch(e => {
        this.errors.push(e)
      })

    axios.get(recommends)
      .then(response => {
        var section = {
          title: 'Claro video te recomienda',
          content: response.data.response.groups
        }

        self.recommends.push(section)
      })
      .catch(e => {
        console.log(e)
      })

    axios.get(olympic)
      .then(response => {
        var section = {
          title: 'Juegos Olímpicos de Invierno 2018',
          content: response.data.response.groups
        }

        self.sections.push(section)
      })
      .catch(e => {
        console.log(e)
      })

    axios.get(bestSeries)
      .then(response => {
        var section = {
          title: 'Las mejores series',
          content: response.data.response.groups
        }

        self.sections.push(section)
      })
      .catch(e => {
        console.log(e)
      })

    axios.get(rentAndSale)
      .then(response => {
        var section = {
          title: 'Novedades en Renta y Venta',
          content: response.data.response.groups
        }

        self.sections.push(section)
      })
      .catch(e => {
        console.log(e)
      })

    axios.get(bestPictures)
      .then(response => {
        var section = {
          title: 'Las mejores películas',
          content: response.data.response.groups
        }

        self.sections.push(section)
      })
      .catch(e => {
        console.log(e)
      })
  },
  name: 'Home'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .home {
    width: 100vw;
    min-height: 100vh;
    background: linear-gradient(to bottom, #ffffff 216px, #f4f3fc);
    background-image: -webkit-linear-gradient(to bottom #ffffff 216px, #f4f3fc);
  }

  .background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    min-width: 100%;
    min-height: 226px;
    height: 226px;
    background-size: cover;
    background-position: top left;
    opacity: 0;
    transition: opacity 0.3s;
  }

  .background.active {
    opacity: 1;
  }

  .VueCarousel-slide .cover {
    position: absolute;
    top: 52px;
    left: 48px;
    max-width: calc(100vw - 96px);
    height: 150px;
    border-radius: 2px;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.5);
  }

  .whiteOverlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    height: 226px;
    background: linear-gradient(to top, #fff, rgba(255, 255, 255, 0.0));
    background-image: -webkit-linear-gradient(to top #fff, rgba(255, 255, 255, 0) 100%);
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
    height: 100%;
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
    margin-top: 24px;
    max-width: calc(100vw - 16px);
    overflow-x: scroll;
  }

  .section .title {
    font-size: 12px;
    padding: 4px;
    color: #9b9b9b;
  }

  .section .movie {
    display: inline-block;
    width: 164px;
    height: 224px;
    background-color: #d8d8d8;
    box-shadow: 0 1px 3px 0 rgba(136, 136, 136, 0.5);
    margin-left: 4px;
  }

  .navbar {
    display: none;
  }

  @media screen and (min-width: 576px) {
    .background {
      height: 413px;
    }

    .whiteOverlay {
      height: 413px;
    }

    .home {
      width: 100vw;
      min-height: 100vh;
      background: linear-gradient(to bottom, #ffffff 413px, #f4f3fc);
      background-image: -webkit-linear-gradient(to bottom #ffffff 413px, #f4f3fc);
    }

    .search {
      position: fixed;
      top: 4px;
      right: 88px;
      z-index: 9001;
      width: 155px;
      height: 36px;
      border-radius: 20px;
      box-shadow: none;
    }

    .search input {
      border-radius: 20px;
      border: 1px solid #e5e5e5;
      font-size: 16px;
    }

    .search i {
      top: 8px;
    }

    .VueCarousel-slide .cover {
      width: auto;
      height: 300px;
      top: 96px;
    }

    /* .section .movie:hover {
      width: 80px;
    } */

  }
</style>
