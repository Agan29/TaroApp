<template>
  <view class="index">
    <view class="container">
      <view class="date-view">
        <text class="date">{{ nowDate }}</text>
        <text class="weeky">{{ weeky }}</text>
      </view>
      <Card />
      <Card />
      <AtButton>按钮文案</AtButton>
    </view>
  </view>
</template>

<script>
import './index.scss'
import Taro from '@tarojs/taro'
import { ref } from 'vue'
import { AtButton } from 'taro-ui-vue'
import Card from '@/components/Card'
import dayjs from 'dayjs'
import 'dayjs/locale/zh-cn'
dayjs.locale('zh-cn')

const weekyMap = {
  0: '星期日',
  1: '星期一',
  2: '星期二',
  3: '星期三',
  4: '星期四',
  5: '星期五',
  6: '星期六'
}
export default {
  components: { AtButton, Card },
  setup() {
    const nowDate = ref(dayjs().format('MM月DD日'))

    const weeky = ref(weekyMap[dayjs().day()])

    return {
      nowDate,
      weeky
    }
  }
}
</script>
