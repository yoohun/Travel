<template>
  <div class="recommend">
    <div class="recommend-title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item of recommend" :key="item.id">
        <img class="item-img" :src="item.imgUrl" alt="">
        <div class="item-content">
          <div class="item-title">{{item.title}}</div>
          <div class="item-text">{{item.desc}}</div>
          <div class="item-price">&#165;<span class="item-prices">{{item.price}}</span> <span class="item-priceqi">起</span></div>
        </div>
      </li>
    </ul>
    <div class="more">查看更多详情</div>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    recommend: Array
  }
}
</script>

<style lang="stylus" scoped>
@import "~styles/mixins.styl"
.recommend-title
  line-height .8rem
  background #f2f2f2
  margin-top .2rem
  text-indent .2rem
.item
  height 1.9rem
  display flex
  overflow hidden
  padding .1rem
  .item-img
    width 1.7rem
    height 1.7rem
    padding .1rem
  .item-content
    padding .2rem
    flex 1
    min-width 0
    .item-title
      line-height .54rem
      font-size .32rem
      ellipsis()
    .item-text
      line-height .4rem
      ellipsis()
    .item-price
      color orangered
      height .65rem
      line-height .75rem
      .item-prices
        font-size .50rem
        padding 0 .05rem
      .item-priceqi
        color #adadad

.more
  color #0486ff
  text-align center
  line-height .8rem
</style>
