<template>
  <div class="goods">
    <goods-list-item v-for="(item,index) in goods" 
                     :goods-item="item" :key="index" />
  </div>
</template>

<script type="text/javascript">
import GoodsListItem from './GoodsListItem'

export default {
  name: "GoodsList",
  components: {
    GoodsListItem
  },
  data() {
    return {
      goods: {
        type: Array,
        default() {
          return []
        }
      }
    }
  }
}
</script>

<style scoped>
  .goods {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;

    padding: 2px;
  }
</style>
