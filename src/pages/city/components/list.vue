<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="buttonlist">
          <div class="buttonwrapper">
            <div class="button">{{this.currentcity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="buttonlist">
          <div class="buttonwrapper" v-for="item of list" :key="item.id" v-on:click="cityclick(item.name)">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div class="item border-bottom" v-for="itemlist of item" :key="itemlist.id" @click="cityclick(itemlist.name)">
              {{itemlist.name}}
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'citylist',
  computed: {
    ...mapState({
      currentcity: 'city'
    })
  },
  props: {
    list: Array,
    cities: Object,
    letter: String
  },
  methods: {
    cityclick (city) {
      this.changecity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changecity'])
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.border-topbottom
  &:before
    border-color: #ccc
  &:after
    border-color: #ccc
.border-bottom
  &:before
    border-color: #ccc
.list
  overflow hidden
  position absolute
  top: 1.58rem
  left: 0
  right 0
  bottom:0
  .title
    line-height .54rem
    width 100%
    padding-left .2rem
    box-sizing border-box
    background #eee
    color: #666
    font-size .26rem
  .buttonlist
    overflow hidden
    padding .1rem .6rem .1rem .1rem
    .buttonwrapper
      width 33.3%
      float left
      .button
        margin .1rem
        padding .1rem 0
        text-align center
        border .02rem solid $bgColor
        border-radius .06rem
  .item-list
    .item
      line-height .6rem
      padding-left .2rem
</style>
