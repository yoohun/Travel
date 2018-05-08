<template>
  <div class="cityheader">
    城市选择
    <router-link to="/">
      <div class="iconfont header-back">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'cityheader'
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.cityheader
  position relative
  color white
  height .86rem
  line-height .86rem
  text-align center
  background $bgColor
  font-size .32rem
  overflow hidden
  .header-back
    position absolute
    left 0
    top 0
    color #ffffff
    width .64rem
    text-align center
    font-size .35rem
</style>
