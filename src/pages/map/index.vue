<template>
  <div>
      <i-tabs :current="current_scroll" scroll @change="handleChangeScroll">
        <i-tab key="tab1" title="选项1"></i-tab>
        <i-tab key="tab1" title="选项2"></i-tab>
        <i-tab key="tab1" title="选项3"></i-tab>
        <i-tab key="tab1" title="选项4"></i-tab>>
        </i-tabs>
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