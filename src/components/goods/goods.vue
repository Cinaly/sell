<template>
<div class="goods">
  <div class="menu-wrapper">
    <ul class="content">
      <li v-for="item in goods" class="menu-item">
          <span class="text border-1px">
            <span class="icon" :class="classMap[item.type]" v-show="item.type>0"></span>
            {{item.name}}
          </span>
      </li>
    </ul>
  </div>
  <div class="foods-wrapper">
    <ul class="content">
      <li v-for="item in goods" class="food-list">
        <h1 class="title">{{item.name}}</h1>
        <ul>
          <li @click="selectFood(food,$event)" v-for="food in item.foods" class="food-item">
            <div class="icon">
              <img :src="food.icon" width="57" alt="">
            </div>
            <div class="content">
              <h2 class="name">{{food.name}}</h2>
              <p class="desc">{{food.description}}</p>
              <div class="extra">
                <span class="count">月售{{food.sellCount}}</span>
                <span>好评率{{food.rating}}%</span>
              </div>
              <div class="price">
                <span class="now">¥ {{food.price}}</span>
                <span class="old" v-show="food.oldPrice">¥ {{food.oldPrice}}</span>
              </div>
            </div>
          </li>
        </ul>
      </li>
    </ul>
  </div>
</div>
<!--<food :food="selectedFood" v-ref:food></food>-->
</template>

<script type="text/ecmascript-6">
  import BScroll from 'better-scroll'
  import food from '../food/food'

  export default{
    props: {
      seller: Object
    },
    data () {
      return {
        goods: [],
        selectedFood: {}
      }
    },
    //   methods: {
//      selectMenu (index, event) {
//        if (!event._constructed) {
//          return
//        }
//        let foodList = this.$els.foofdWrapper.getElementsByClassName('food-list-hook')
//        let el = foodList[index]
//        this.foodScore.scrollToElement(el, 300)
//      },
    //     selectFood (food, event) {
    //      if (!event._counstruted) {
    //        return
    //     }
    //      this.selectedFood = food
    // this.$refs.
    //    }
    //  },
    created () {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
      this.$http.get('../../data.json').then((data) => {
        data = data.body
        this.goods = data.goods
        this._initScroll()
        console.log(this.goods)
      })
    },
    methods: {
      _initScroll () {
        const menuScroll = new BScroll('.menuWrapper')
        const foodsScroll = new BScroll('.foodWrapper')
      }
    },
    components: {
      food
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixin.styl"
  .goods
    display: flex
    overflow: hidden
    position: absolute
    top: 174px
    bottom: 46px
    width: 100%
    .menu-wrapper
      flex: 0 0 80px
      width: 80px
      background: #f3f5f7
      .menu-item
        display: table
        height: 54px
        width: 56px
        line-height: 14px
        padding: 0 12px
        .icon
          display: inline-block
          vertical-align: top
          width: 12px
          height: 12px
          margin-right: 2px
          background-size: 12px 12px
          background-repeat: no-repeat
          &.decrease
            bg_image('decrease_3')
          &.discount
            bg_image('discount_3')
          &.guarantee
            bg_image('guarantee_3')
          &.invoice
            bg_image('invoice_3')
          &.special
            bg_image('special_3')
        .text
          display: table-cell
          width: 56px
          vertical-align: middle
          border-1px(rgba(7, 17, 27, 0.1))
          font-size: 12px
    .foods-wrapper
      flex: 1
      .title
        padding-left: 14px
        height: 26px
        line-height: 26px
        border-left: 2px solid #d9dde1
        font-size: 12px
        color: rgb(147, 153, 159)
        background: #f3f5f7
      .food-item
        display: flex
        margin: 18px
        padding-bottom: 18px
        border-1px(rgba(7, 17, 27, 0.1))
        &:last-child
          border-none()
          margin-bottom: 0
        .icon
          flex: 0 0 57px
          margin-right: 10px
        .content
          flex: 1
          .name
            margin: 2px 0 8px
            height: 14px
            line-height: 14px
            font-size: 14px
            color: rgb(7, 17, 27)
          .desc, .extra
            line-height: 10px
            font-size: 10px
            color: rgb(147, 153, 159)
          .desc
            margin-bottom: 8px
          .extra
            .count
              margin-right: 12px
          .price
            font-weight: 700
            line-height: 24px
            .now
              margin-right: 8px
              font-size: 14px
              color: rgb(240, 20, 20)
            .old
              text-decoration: line-through
              font-size: 10px
              color: rgb(147, 153, 159)

</style>
