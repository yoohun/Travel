<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showswiper">
      <swiper-slide v-for="ittem of swiper" :key="ittem.id">
        <img class="swiper-img" :src="ittem.imgUrl" alt="">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    swiper: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  },
  computed: {
    showswiper () {
      return this.swiper.length
    }
  }
}
</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active
  background :#ffffff
.wrapper
  width: 100%
  height :0
  overflow :hidden
  padding-bottom :31.25%
  background :#eaeaea
  .swiper-img
    width : 100%
</style>
