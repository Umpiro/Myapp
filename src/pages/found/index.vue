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
      found:[]
    }
  },
  onLoad (option){
    this.found = require(option.type + '.json')
    console.log(this.found)
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
