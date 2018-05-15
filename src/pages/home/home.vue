<template>
  <div>
    <div class="home">
      <home-header></home-header>
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
import { mapState } from 'Vuex'
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
      lastcity: '',
      swiper: [],
      icons: [],
      recommend: [],
      weekend: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getinfor () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getuindesinfor)
    },
    getuindesinfor (res) {
      res = res.data
      if (res.data && res.ret) {
        this.swiper = res.data.swiperList
        this.icons = res.data.iconList
        this.recommend = res.data.recommendList
        this.weekend = res.data.weekendList
      }
    }
  },
  mounted () {
    this.lastcity = this.city
    this.getinfor()
  },
  activated () {
    if (this.lastcity !== this.city) {
      this.lastcity = this.city
      this.getinfor()
    }
  }
}
</script>

<style>

</style>
