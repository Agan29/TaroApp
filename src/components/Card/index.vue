<template>
  <view class="card-wrap">
    <view class="card-text" :class="textPosition">
      <text class="card-des" v-if="des">{{ des }}</text>
      <text class="card-title" v-if="title">{{ title }}</text>
    </view>
    <view class="card-bg">
      <image
        src="https://camo.githubusercontent.com/3e1b76e514b895760055987f164ce6c95935a3aa/687474703a2f2f73746f726167652e333630627579696d672e636f6d2f6d74642f686f6d652f6c6f676f2d3278313531333833373932363730372e706e67"
      />
    </view>
  </view>
</template>

<script lang="ts">
import './index.scss'
import { defineComponent } from 'vue'
// import { reactive, toRefs, watch } from 'vue'

export default defineComponent({
  name: 'Card',
  components: {},
  props: {
    textPosition: { type: String, default: 'top' },
    des: { type: String },
    title: { type: String, required: true }
  }
  // setup(props, context) {
  //   console.log(props, context)
  //   const { des = '', title = '' } = props
  //   return {
  //     des,
  //     title
  //   }
  // }
})
</script>

