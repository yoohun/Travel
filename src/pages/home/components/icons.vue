<template>
  <div class="icon">
    <swiper :options="swiperOption">
      <swiper-slide class="iconswiper" v-for="(page,index) of pages" :key="index">
        <div class="iconDiv" v-for="ttem of page" :key="ttem.id">
          <div class="iconImg">
            <img class="iconImgContent" :src="ttem.imgUrl">
          </div>
          <p class="iconDesc">{{ttem.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>

export default {
  name: 'inconImg',
  props: {
    icons: Array
  },
  data () {
    return {
      swiperOption: {
        autoPlay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.icons.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
  .icon >>> .iconswiper
    width 100%
    height 0
    padding-bottom 50%
    overflow hidden
    position relative
  .icon
    margin-top .2rem
    .iconDiv
      position relative
      width 25%
      padding-bottom  25%
      float left
      overflow hidden
      .iconImg
        position absolute
        left: 0
        right: 0
        top: 0
        bottom .44rem
        .iconImgContent
          height 100%
          display block
          box-sizing border-box
          padding .1rem
          margin: 0 auto
      .iconDesc
        position absolute
        left 0
        right 0
        bottom:0
        height .44rem
        text-align center
        color $darkTextColor
        ellipsis()
</style>
