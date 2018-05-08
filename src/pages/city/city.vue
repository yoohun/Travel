<template>
  <div>
    <cityheader></cityheader>
    <citysearch></citysearch>
    <citylist :list="hotcity" :cities="cities" :letter="letter"></citylist>
    <cityalphabet :cities="cities" @change="changeletter"></cityalphabet>
  </div>
</template>

<script>
import cityheader from './components/cityheader'
import citysearch from './components/search'
import citylist from './components/list'
import cityalphabet from './components/alphabet'
import axios from 'axios'
export default {
  name: 'city',
  data () {
    return {
      hotcity: [],
      cities: {},
      letter: ''
    }
  },
  components: {
    cityheader,
    citysearch,
    citylist,
    cityalphabet
  },
  methods: {
    getCityinfor () {
      axios.get('/api/city.json')
        .then(this.handlecity)
    },
    handlecity (res) {
      res = res.data
      if (res.ret && res.data) {
        this.hotcity = res.data.hotCities
        this.cities = res.data.cities
      }
    },
    changeletter (letter) {
      this.letter=letter
    }
  },
  mounted () {
    this.getCityinfor()
  }
}
</script>

<style lang="stylus" scoped>

</style>
