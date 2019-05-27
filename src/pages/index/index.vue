<template>
  <div>
    <i-notice-bar icon="systemprompt" loop>
      {{notice}}珍藏你的回忆时刻
      </i-notice-bar>
    <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
      style="height:200px"
    >
    <block v-for="item in imgUrls" :key="item">
      <swiper-item>
        <image :src="item" style="width:100%;"/>
      </swiper-item>
    </block>
  </swiper>
    <i-grid>
      <i-grid-item @click="goType(1)" i-class="no-border"  :key="item" >
        <i-grid-icon>
          <image src="/static/tabs/faxian.png" />
           </i-grid-icon>
            <i-grid-label>发现</i-grid-label>
             </i-grid-item>
             
      <i-grid-item  @click="goType(2)" i-class="no-border"  :key="item" >
        <i-grid-icon>
          <image src="/static/tabs/haoyou.png" />
           </i-grid-icon>
            <i-grid-label>好友</i-grid-label>
            
             </i-grid-item>
            </i-grid>
             <i-panel title="精彩推荐">
               <view class="top-padding">
                  <view :key='item' class="top-padding">
                 <i-card :title=清爽一夏 :extra=风景 thumb="/static/tabs/timg.jpg">
                 <view slot="content">欣赏时刻</view>
                 <view slot="footer">2017年夏</view>
                </i-card>
                  </view>
                  <view :key='item' class="top-padding">
                 <i-card :title=圣诞节回忆 :extra=人物 thumb="/static/tabs/timg.jpg">
                 <view slot="content">欣赏时刻</view>
                 <view slot="footer">2018.12.25</view>
                </i-card>
                  </view>
                   <view :key='item' class="top-padding">
                 <i-card :title=艺术展 :extra=静物 thumb="/static/tabs/timg.jpg">
                 <view slot="content">欣赏时刻</view>
                 <view slot="footer">2019.1</view>
                </i-card>
                  </view>
                  
               </view>
            </i-panel>
        
        </div>
    
</template>

<script>
import card from '@/components/card'

export default {
  
  data () {
    return {
      title_name: "热门",
      grids: [
        {title:"外卖",image:"/static/images/1.png"},
        {title:"零食",image:"/static/images/2.png"}
      ],
      imgUrls: [
        '/static/images/person.jpg',
        '/static/images/person2.jpg',
        '/static/images/sky.jpg'
      ],
       
      
      ShowTime:[],
         notice: '',
    }
  },
 
  components: {
    card
  },

  methods: {
    goType(type){
      console.log(type)
      let url = '../list/main?type=' + type
      mpvue.navigateTo({ url })
    },
    clickHandle (ev) {
      console.log('clickHandle:', ev)
      // throw {message: 'custom test'}
    }
  },

  created () {
    const db = wx.cloud.database({ env: 'memory-467816'})
    db.collection('ShowTime').get().then(
      res => {
        console.log(res)
        this.ShowTime = res.data
      }
    )
    wx.cloud.callFunction({ name: 'me' }).then(
      res => {console.log(res)}
    )
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
