<template>
  <div class="vlp-detail-class">
    <div class="vlp-detail-item" v-for="(item,index) in data" :key="index">
      <span class="title">{{item.label}}</span>：<span class="value">{{item.value}}</span>
      <span class="tip" v-for="(tip,i) in item.tips" :key="i" v-html="tip"></span>
      <slot></slot>
      </div>
  </div>
</template>
<script>
export default {
  name: 'VlpDetail',
  props: {
    data: {
      type: Array,
      required: true
    }
  }
}
</script>
<style lang="less" scoped>
  .vlp-detail-class{
    font-size:14px;
    color: #666666;
    text-indent: 14px;
    padding: 0;
    .vlp-detail-item{
      padding-top: 15px;
    }
  }
</style>
