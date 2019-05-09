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
      <i-grid-item @click="goList(item.url)" i-class="no-border" v-for="item in grids" :key="item" >
        <i-grid-icon>
          <image src="/static/tabs/faxian.png" />
           </i-grid-icon>
            <i-grid-label>发现</i-grid-label>
             </i-grid-item>
             
      <i-grid-item  @click="goList(item.url)" i-class="no-border" v-for="item in grids" :key="item" >
        <i-grid-icon>
          <image src="/static/tabs/haoyou.png" />
           </i-grid-icon>
            <i-grid-label>好友</i-grid-label>
            
             </i-grid-item>
            </i-grid>
             <i-panel title="精彩推荐">
               <view class="top-padding">
                  <view v-for="item in ShowTime" :key='item' class="top-padding">
                 <i-card :title="item.name" :extra="item.type" thumb="/static/tabs/photo.png">
                 <view slot="content">欣赏时刻</view>
                 <view slot="footer">{{item.time}}</view>
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
      imgUrls: [
        '/static/images/person.jpg',
        '/static/images/person2.jpg',
        '/static/images/sky.jpg'
      ],
       grids: [
        {type:'烧烤',img:'/static/tabs/extra.png',"url":'../found/main?type=1'},
        
        
      ],
      
      ShowTime:[],
         notice: '',
    }
  },
 
  components: {
    card
  },

  methods: {
    goList (url) {
      mpvue.navigateTo({ url })
    },
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
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
