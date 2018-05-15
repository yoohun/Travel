<template>
  <div>
    <div class="searchk">
      <input v-model="keyword" type="text" class="searchipt" placeholder="输入城市名或拼音">
    </div>
    <div class="searchcontent" ref="searchlist" v-show="keyword">
      <ul>
        <li class="searchli border-bottom" v-for="item of list" :key="item.id" @click="cityclick(item.name)">{{item.name}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapMutations } from 'vuex'
export default {
  name: 'citysearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  methods: {
    cityclick (city) {
      this.changecity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changecity'])
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.searchlist)
  }
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
.searchcontent
  position absolute
  top 1.58rem
  left 0
  bottom 0
  right  0
  overflow hidden
  z-index 1
  /*background #eee*/
  .searchli
    line-height .62rem
    padding-left .2rem
    color #fff
    background $bgColor
</style>
