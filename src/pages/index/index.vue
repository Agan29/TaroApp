<template>
  <view class="index">
    <view class="container">
      <view class="date-view">
        <text class="date">{{ nowDate }}</text>
        <text class="weeky">{{ weeky }}</text>
      </view>
      <template v-if="status === 'loading'">
        <AtLoadMore :status="status" />
      </template>

      <view>
        <Card
          v-for="card in cards"
          :key="card.key"
          :title="card.title"
          :des="card.des"
          @tap="(e) => handleClick(e, card)"
        />
      </view>
    </view>
  </view>
</template>

<script>
import './index.scss'
import Taro from '@tarojs/taro'
import { reactive, ref, onBeforeMount, toRefs } from 'vue'
import { AtLoadMore } from 'taro-ui-vue3'
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
  nameL: 'Home',
  components: { AtLoadMore, Card },
  setup() {
    const nowDate = ref(dayjs().format('MM月DD日'))

    const weeky = ref(weekyMap[dayjs().day()])

    const state = reactive({
      cards: [],
      status: 'loading'
    })

    const getCardData = () => {
      setTimeout(() => {
        state.status = 'noMore'
        state.cards = [
          {
            title: 'this is title',
            des: 'this is des',
            textPosition: 'top',
            key: 'card-1'
          },
          {
            title: 'this is title2',
            des: 'this is des2',
            textPosition: 'top',
            key: 'card-2'
          }
        ]
      }, 2000)
    }

    const handleClick = (e, card) => {
      Taro.navigateTo({
        url: `/pages/detail/index?id=${card.key}`
      })
    }
    onBeforeMount(getCardData)
    return {
      nowDate,
      weeky,
      handleClick,
      ...toRefs(state)
    }
  }
}
</script>
