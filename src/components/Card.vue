<template>
  <a :href="detailUrl">
    <div class="book-card">
      <div class="thumb" @click.stop="previwImg(book.image)">
        <img
          :src="book.image"
          class="image"
          mode="aspectFit"
        >
      </div>
      <div class="detail">
        <div class="row text-primary">
          <div class="left">
            {{book.title}}
          </div>
          <div class="right">
            {{book.rate}} <Rate :value="book.rate"></Rate>
          </div>
        </div>
        <div class="row">
          <div class="left">
            {{book.author}}
          </div>
          <div class="right">
            浏览量:{{book.count}}
          </div>
        </div>
        <div class="row">
          <div class="left">
            {{book.publisher}}
          </div>
          <div class="right">
            {{book.nickName}}
          </div>
        </div>
      </div>
    </div>
  </a>
</template>

<script>
import Rate from '@/components/Rate'
export default {
  props: {
    book: Object
  },
  components: {
    Rate
  },
  computed: {
    detailUrl () {
      return `/pages/detail/main?id=${this.book.id}` // ?带代表传递的参数
    }
  },
  methods: {
    previwImg (imgUrl) {
      wx.previewImage({
        urls: [imgUrl]
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
.book-card
  display: flex
  margin: 10rpx 0
  padding: 20rpx
  display: flex
  .thumb
    overflow: hidden
    width: 180rpx
    height: 180rpx
    display: flex
    .image
      max-height: 100%  // 基于父元素宽度
      max-width: 100%    // 基于父元素高度
      justify-content: center
      align-items: center
  .detail
    width:100%
    padding: 10rpx 20rpx
    .row
      display: flex
      justify-content: space-between
      width: 100%
      padding: 10rpx
      font-size: 25rpx
      .left
        max-width: 70%
</style>
