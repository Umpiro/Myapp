<template>
  <div>    
<i-panel title="搜索照片">
    <i-input placeholder="请输入你想搜索的关键字" />
</i-panel>
 <i-panel title="添加相册">
               <view class="top-padding">
                 <i-card title="风景类" extra="点击添加" thumb="/static/tabs/风景.png">              
                 <view slot="footer">点击添加</view>
                </i-card>
               </view>
               <view class="top-padding">
                 <i-card title="人像类" extra="点击添加" thumb="/static/tabs/人像.png">              
                 <view slot="footer">点击添加</view>
                </i-card>
               </view>
               <view class="top-padding">
                 <i-card title="物品类" extra="点击添加" thumb="/static/tabs/物品.png">              
                 <view slot="footer">点击添加</view>
                </i-card>
               </view>
               <view class="top-padding">
                 <i-card title="其他" extra="点击添加" thumb="/static/tabs/其他.png">              
                 <view slot="footer">点击添加</view>
                </i-card>
               </view>
            </i-panel>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  components: {
    card
  },

  data () {
    return {
      current_scroll: 'tab1',
      motto: 'Hello miniprograme',
    }
  },
   components: {
    card
  },

  methods: {
    handleChangeScroll (event) {
     console.log(event)
     this.current_scroll = event.mp.detail.key
      
    }
  },

  created () {
    // let app = getApp()
  }
}
</script>

<style scoped>
div >>>.no-border {
 border-width: 0pt;
}
div >>>.top-padding {
  margin-top: 20pt;
}
</style>