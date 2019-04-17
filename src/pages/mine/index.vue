<template>
  <div>
    <view class="userinfo">
      <view class="userinfo-avatar">
    <open-data  size="small" shape="square" type="userAvatarUrl" ></open-data>
    </view>
    <open-data type="userNickName"></open-data>
    </view>
    <i-cell-group>
      </i-cell-group>
     <i-cell-group>
    <i-cell title="通知" is-link></i-cell>
    <i-cell title="编辑资料" is-link url="/pages/dashboard/index"></i-cell>
    <i-cell title="帮助与设置" is-link url="/pages/dashboard/index" only-tap-footer></i-cell>
    <i-cell title="共享相册">
        <switch slot="footer" checked />
    </i-cell>
</i-cell-group>
<i-button bind:click="handleClick" type="success" shape="circle">退出登录</i-button>
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
