<template>
  <div class='wrapper'>
    <swiper :swiperList='recommends'><div>111</div></swiper>
  </div>
</template>
<script>
import swiper from 'base/swiper/swiper.vue'
import {getRecommend} from 'api/recommend'
import {ERR_OK} from 'api/config'
export default {
  name: 'recommend',
  components: {
    swiper
  },
  data () {
    return {
      recommends: []
    }
  },
  created () {
    this.getRecommend()
  },
  methods: {
    getRecommend () {
      getRecommend().then(res => {
        if (res.code === ERR_OK) {
          this.recommends = res.data.slider
          console.log(this.recommends)
        }
      })
    }
  }
}
</script>
<style lang="stylus" scoped>
</style>
