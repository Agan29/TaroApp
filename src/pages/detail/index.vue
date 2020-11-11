<template>
  <view>
    <text>this is detail</text>
    <text>{{ id }}</text>
  </view>
</template>

<script>
import { reactive, toRefs, watch } from 'vue'
import { getCurrentInstance } from '@tarojs/taro'
export default {
  name: 'detail',
  components: {},
  props: {},
  setup(props, context) {
    const { id } = getCurrentInstance().router.params
    console.log(props, context)

    return { id }
  }
}
</script>
<style lang='scss'>
</style>
