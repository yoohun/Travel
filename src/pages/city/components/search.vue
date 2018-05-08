<template>
  <div class="searchk">
    <input type="text" class="searchipt" placeholder="输入城市名或拼音">
  </div>
</template>

<script>
export default {
  name: 'citysearch'
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.searchk
  height .72rem
  padding 0 .2rem
  background $bgColor
  .searchipt
    height .62rem
    line-height .62rem
    width 100%
    text-align center
    border-radius .05rem
    padding 0 .05rem
    box-sizing border-box
    color #666
</style>
