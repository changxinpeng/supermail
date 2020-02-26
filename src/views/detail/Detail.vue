<template>
  <div>
    <detail-nav-bar/>
    <detail-swiper :top-images="topImages" />
  </div>
</template>

<script type="text/javascript">
  import DetailNavBar from './childComps/DetailNavBar'
  import DetailSwiper from './childComps/DetailSwiper'

  import {getDetail, Goods} from "network/detail"

  export default {
    name: "Detail",
    components: {
      DetailNavBar,
      DetailSwiper
    },
    data() {
      return {
        iid: null,
        topImages: [],
        goods: null
      }
    },
    created() {
      //储存商品id
      this.iid = this.$route.params.iid
      //根据id请求数据
      getDetail(this.iid).then(res => {
        const data = res.result;
        //获取顶部商品图片轮播图
        this.topImages = data.itemInfo.topImages

        //获取商品信息
        this.goods = new Goods(data.itemInfo, data.columns, data.shopInfo.services)
      })
    }
  }
</script>

<style scoped>
</style>
