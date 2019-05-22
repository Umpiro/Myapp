<template>
  <div>
     <i-card v-for="item in list" :key="item" i-class="split" :extra="item.name" :thumb="item.image">
          <view slot="content">{{item.remark}}</view>
          <view slot="footer">{{item.address}}</view>
      </i-card>
  </div>
</template>

<script>


export default {

  data () {
    return {
      list:[]
    }
  },

  onLoad (option){
    var type ='发现'
    console.log('option: ',option)
    if (option.type==1){
      type='发现'
    }
    if (option.type==2){
      type='好友'
    }
    this.list = require( '@/data/'+type + '.json')
    console.log(this.list)
  },
  methods: {

  },
  created () {
  }
}
</script>

<style scoped>
div >>> .split {
  margin-bottom: 10pt;
}
</style>