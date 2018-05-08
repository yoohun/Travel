<template>
  <div>
    <div class="home">
      <home-header :city="city"></home-header>
      <home-swiper :swiper="swiper"></home-swiper>
      <icons-img :icons="icons"></icons-img>
      <home-recommend :recommend="recommend"></home-recommend>
      <home-weekend :weekend="weekend"></home-weekend>
    </div>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/HomeSwiper'
import iconsImg from './components/icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
export default {
  name: 'home',
  components: {
    HomeHeader,
    HomeSwiper,
    iconsImg,
    HomeRecommend,
    HomeWeekend
  },
  data () {
    return {
      city: '',
      swiper: [],
      icons: [],
      recommend: [],
      weekend: []
    }
  },
  methods: {
    getinfor () {
      axios.get('/api/index.json')
        .then(this.getuindesinfor)
    },
    getuindesinfor (res) {
      res = res.data
      if (res.data && res.ret) {
        this.city = res.data.city
        this.swiper = res.data.swiperList
        this.icons = res.data.iconList
        this.recommend = res.data.recommendList
        this.weekend = res.data.weekendList
      }
    }
  },
  mounted () {
    this.getinfor()
  }
}
</script>

<style>

</style>
