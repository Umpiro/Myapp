<template>
  <div>
    <view class="userinfo">
      <view class="userinfo-avatar">
    <open-data type="userAvatarUrl"></open-data>
    </view>
    <open-data type="userNickName"></open-data>
    </view>
    <i-cell-group>
      </i-cell-group>
        </div>
    
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
         motto: 'Hello miniprograme',
         userInfo: {
           nickName: 'mpvue',
           avatarUrl: 'http://mpvue.com/assets/logo.png'
         }
    }
  },

  components: {
    card
  },

  methods: {
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
