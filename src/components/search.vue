<template>
<div class="search-list-class">
  <van-sticky>
    <van-nav-bar
class="search-nav-bar-class"
>
  <Search
  slot="title"
  v-model="searchValue"
  class="search-class"
  :tipInterface="searchListInterface"
  placeholder="搜索名称"
  :historyList="historyList"
  :autoHidden="false"
  :displayVisible = "true"
  :autoShowHistory="true"
  @search="searchFun"
  @cancel="cancel"
  @deleteHistory="deleteHistory"></Search>
</van-nav-bar>

</van-sticky>

  <List
  :interface-fun="searchList"
  :columns = "columns"
  :parameter = "parameter"
  :autoLoad="false"
  ></List>

</div>

</template>
<script>
import { NavBar, Icon, Row, Sticky } from 'vant'
import List from '../../packages/components/list/list.vue'
import Search from '../../packages/components/search/search.vue'
import { cardLabel } from './list.js'
import { searchListObj, searchList } from '../api/listPage.js'
export default {
  components: {
    List,
    Search,
    [NavBar.name]: NavBar,
    [Icon.name]: Icon,
    [Row.name]: Row,
    [Sticky.name]: Sticky
  },
  data() {
    return {
      searchList: searchListObj,
      searchListInterface: searchList,
      columns: cardLabel,
      searchValue: '',
      historyList: ['中国', '阿斯利康大家发生的'],
      parameter: {}
    }
  },
  methods: {
    searchFun(v) {
      this.parameter = { name: v }
      console.log('searchFun', v)
    },
    cancel() {
      this.$router.go(-1)
    },
    deleteHistory() {
      this.historyList = []
    }
  }
}
</script>
<style lang="less" scoped>
.search-list-class{
  .search-nav-bar-class{
    .van-nav-bar__title{
      max-width:100%
    }
  }
  .search-class{
   position: absolute;
  }
  .van-pull-refresh__head{
    height: 200px;
  }
}

</style>
