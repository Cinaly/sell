<template>
  <div class="shopcart">
    <div class="content">
      <div class="content-left">
        <div class="logo-wrapper">
          <div class="logo">
            <i class="icon-shopping_cart"></i>
          </div>
        </div>
        <div class="price">¥ {{totalPrice}}</div>
        <div class="desc">另需配送费 ¥ {{deliverPrice}} 元</div>
      </div>
      <div class="content-right">
        <div class="pay">
          ¥ {{minPrice}}元起送
        </div>
      </div>
    </div>
    <div class=""></div>
    <div class=""></div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default{
    props: {
      selectFoods: {
        type: Array,
        default () {
          return [{price: 10, count: 1}]
        }
      },
      deliverPrice: {
        type: Number,
        default: 0
      },
      minPrice: {
        type: Number,
        default: 0
      }
    },
    computed: {
      totalPrice () {
        let total = 0
        this.selectFoods.forEach((food) => {
          total += food.price * food.count
        })
        return total
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .shopcart
    position: fixed
    bottom: 0
    left: 0
    z-index: 50
    width: 100%
    height: 48px
    .content
      display: flex
      background: #141d27
      font-size: 0
      .content-left
        flex: 1
        .logo-wrapper
          display inline-block
          position: relative
          top: -10px
          margin: 0 12px
          padding: 6px
          width: 56px
          height: 56px
          box-sizing: border-box
          vertical-align: top
          border-radius: 50%
          background: #141d27
          .logo
            width: 100%
            height: 100%
            border-radius: 50%
            background: #2b343c
            text-align: center
            .icon-shopping_cart
              font-size: 24px
              color: #80858a
              line-height: 44px
        .price
          display inline-block
          vertical-align: top
          line-height: 24px
          margin-top: 12px
          font-size: 16px
          font-weight: 700
          padding-right: 12px
          box-sizing: border-box
          color: rgba(255, 255, 255, 0.3)
          border-right: 1px solid rgba(255, 255, 255, 0.1)
        .desc
          display inline-block
          margin: 12px 0 0 12px
          line-height: 24px
          font-size: 10px
          vertical-align: top
          color: rgba(255, 255, 255, 0.4)
      .content-right
        flex: 0 0 105px
        width: 105px
        background: #2b333b
        text-align: center
        .pay
          font-size: 12px
          color: rgba(255, 255, 255, 0.4)
          line-height: 48px
          height: 48px
          font-weight: 700
</style>
