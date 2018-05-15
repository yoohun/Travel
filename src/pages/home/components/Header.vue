<template>
    <div class="header">
      <div class="header-left">
        <div class="iconfont">&#xe624;</div>
      </div>
      <div class="header-input">
        <span class="iconfont">&#xe632;</span>
        输入城市/景点/游玩主题
      </div>
      <router-link to="/city">
        <div class="header-right">
          {{this.city}}<span class="iconfont city-icon">&#xe64a;</span>
        </div>
      </router-link>
    </div>
</template>

<script type="text/ecmascript-6">
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
  /*.header{*/
    /*background: #25a4bb;*/
    /*color: #ffffff;*/
    /*line-height: .84rem;*/
    /*display: flex;*/
  /*}*/
  /*.header-left{*/
    /*width: .64rem;*/
    /*float: left;*/
  /*}*/
  /*.header-input{*/
    /*flex: 1;*/
    /*color: #ccc;*/
    /*background: #ffffff;*/
    /*border-radius: .1rem;*/
    /*margin-top: .12rem;*/
    /*margin-left: .2rem;*/
    /*height: .64rem;*/
    /*line-height: .64rem;*/
  /*}*/
  /*.header-right{*/
    /*float: right;*/
    /*width: 1.24rem;*/
    /*text-align: center;*/
  /*}*/
.header
  background: $bgColor;
  color: #ffffff;
  height : .84rem;
  display: flex
  line-height : .84rem
  .header-left
    width: .64rem;
    float: left;
    text-align center
  .header-input
    color: #ccc;
    flex: 1;
    background #ffffff;
    border-radius: .1rem;
    margin-top : .12rem;
    margin-left: .2rem;
    line-height: .64rem;
    height:.64rem;
    text-align:left;
  .header-right
    float: right;
    min-width: 1.04rem;
    padding 0 .1rem
    text-align center;
    color #ffffff
    .city-icon
      font-size: .14rem
      margin-left: .1rem
</style>
