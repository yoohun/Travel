<template>
  <ul class="item-list" >
    <li class="item" v-for="(item,key) of cities" :key="key" @click="letterclick">{{key}}</li>
  </ul>
</template>

<script>
export default {
  name: 'cityalphabet',
  props: {
    cities: Object
  },
  methods: {
    letterclick (e) {
      this.$emit('change', e.target.innerText)
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.item-list
  display flex
  flex-direction column
  justify-content center
  position absolute
  top 1.58rem
  right:0
  bottom 0
  width .4rem
  .item
    color $bgColor
    text-align center
    line-height .4rem
</style>
