<template>
  <view class="product-item-3">
    <view class="product-list-cont" v-for="(item, index) in viewModel" :key="index" @click="linkto(item)">
      <view class="product-list-image">
        <img :src="$api.baseUrl()+item.thumbnailUrl" v-lazy alt="" srcset="">
      </view>
      <view class="product-list-title">{{item.name}}</view>
      <view class="product-list-foot">
        <view class="product-list-price">￥{{item.price}}</view>
        <view class="product-list-lastprice">{{item.marketPrice}}</view>
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    props: {
      viewModel: {}
    },
    methods: {
      toProductShow (item) {
      },
      // 下拉菜单事件
      scrollView () {
      },
      linkto (item) {
        this.$api.to(`/product/show?id=${item.id}`)
      }
    }
  }
</script>


<style lang="scss">
  .product-item-3 {
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    padding: 5px;
    box-sizing: border-box;
    .product-list-cont {
      cursor: pointer;
      width: 46.8%;
      box-sizing: border-box;
      background: #fff;
      box-shadow: 0 1px 15px 1px rgba(69, 65, 78, 0.1);
      margin: 1.6%;
      display: flex;
      flex-wrap: wrap;
      padding: 10px;
      .product-list-image {
        width: 100%;
        flex-grow: 2;
        img {
          width: 100%;
          height: 145px;
        }
      }
      .product-list-title {
        width: 100%;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        font-size: 16px;
        font-weight: 700;
      }
      .product-list-foot {
        .product-list-price {
          font-weight: 600;
          font-size: 18px;
          color: #ee2c28;
          display: inline-block;
        }
        .product-list-lastprice {
          font-size: 12px;
          margin-left: 10px;
          color: #999;
          display: inline-block;
          text-decoration: line-through;
        }
      }
    }
  }
</style>
