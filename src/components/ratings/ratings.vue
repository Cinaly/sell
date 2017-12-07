<template>
  <div class="ratings">
    <div class="ratings-content">
      <div class="overview">
        <div class="overview-left">
          <h1 class="score">{{seller.score}}</h1>
          <div class="title">综合评分</div>
          <div class="rank">高于周边商家{{seller.rankRate}}%</div>
        </div>
        <div class="overview-right">
          <div class="score-wrapper">
            <span class="title">服务态度</span>
            <star :size="36" :score="seller.serviceScore"></star>
            <span class="score">{{seller.serviceScore}}</span>
          </div>
          <div class="score-wrapper">
            <span class="title">商品评分</span>
            <star :size="36" :score="seller.foodScore"></star>
            <span class="score">{{seller.foodScore}}</span>
          </div>
          <div class="delivery-wrapper">
            <span class="title">送达时间</span>
            <span class="deliveryTime">{{seller.deliveryTime}}分钟</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import star from '../star/star'

  export default{
    props: {
      seller: {
        type: Object
      }
    },
    components: {
      star
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .ratings
    position: absolute
    top: 174px
    bottom: 0
    left: 0
    width: 100%
    overflow: hidden
    .overview
      display: flex
      padding: 18px 0
      .overview-left
        padding :6px 0
        flex: 0 0 137px
        width: 137px
        text-align :center
        border-right: 1px solid rgba(7, 17, 27, 0.1)
        .score
          font-size :24px
          line-height: 28px
          color:rgb(255,153,0)
          margin-bottom: 6px
        .title
          font-size: 12px
          line-height 12px
          color:rgb(7,17,27)
          margin-bottom :8px
        .rank
          font-size :10px
          line-height :10px
          color: rgb(147,153,159)
      .overview-right
        flex: 1
        .score-wrapper
          line-height: 18px
          font-size: 12px
          margin-bottom: 8px
          font-size :0
          .title
            font-size :12px
            color: rgb(7,17,27)
          .star
            display :inline-block
            margin:0 12px
            vertical-align :top
          .score
            color: rgb(255,153,0)
            vertical-align :top
            font-size :12px
</style>
