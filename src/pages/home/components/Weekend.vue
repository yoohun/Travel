<template>
  <div>
    <div class="weekend">周末去哪儿</div>
    <div class="weekenditem" v-for="item of weekend" :key="item.id">
      <div class="weekendimg">
        <img class="weekend-img" :src="item.imgUrl" alt="">
      </div>
      <div class="weekend-text">
        <div class="weekend-title">{{item.title}}</div>
        <div class="weekend-desc">{{item.desc}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    weekend: Array
  }
}
</script>

<style lang="stylus" scoped>
.weekend
  line-height .8rem
  background #f2f2f2
  text-indent .2rem
.weekendimg
  height 0
  padding-bottom 34%
  overflow hidden
  background #25a4bb
  .weekend-img
    width 100%
.weekend-text
  margin-top .2rem
  text-indent .2rem
  padding-bottom .2rem
  .weekend-title
    line-height .6rem
    font-size :.32rem
    ellipsis()
  .weekend-desc
    line-height .5rem
    font-size .28rem
    ellipsis()
</style>
