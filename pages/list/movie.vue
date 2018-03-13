<template>
  <section class="container">
    <div class="index">
      <!-- <div class="i-header">
        <i class="icon-category icon iconfont  i-cate"></i>
      </div> -->
      <!-- <Tabs></Tabs> -->
      <div class="i-content">
        <div class="c-item" v-for="item in pageInfo" :key='item.id'>
          <nuxt-link :to="{name:'detail',query:{'item_id': item.item_id}}">
            <div class="i-title">{{item.title}}</div>
            <p class="i-author">作者/{{item.author.user_name? item.author.user_name: "佚名"}}</p>
            <img class="i-img" :src="item.img_url" alt="">
            <p class="i-des">{{item.forward}}</p>
          </nuxt-link>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Tabs from "~/components/tabs.vue"
var axios = require('axios')
export default {
  data(){
    return{
      dateNum: [],
      pageInfo: []
    }
  },
  asyncData (context) {
    return { type:context.query.type}
  },
  components: {
    Tabs
  },
  created () {
    this.getDateNum()
  },
  methods: {
    getDateNum: function () {
      var _this = this
      axios({
          method:'get',
          url:'http://v3.wufazhuce.com:8000/api/onelist/idlist/?channel=wdj&version=4.0.2&uuid=ffffffff-a90e-706a-63f7-ccf973aae5ee&platform=android',
        })
          .then(function(res) {
            _this.dateNum = res.data.data
            console.log(res.data.data)  
            _this.getDateList(_this.dateNum[0])
        });
    },
    getDateList: function(date) {
      var _this = this
      axios({
        method:'get',
        url:'http://v3.wufazhuce.com:8000/api/channel/movie/more/0?channel=wdj&version=4.0.2&uuid=ffffffff-a90e-706a-63f7-ccf973aae5ee&platform=android'
      })
        .then(function(res) {
            _this.pageInfo = res.data.data
          console.log(_this.pageInfo)
      });
    }
  }
}
</script>

<style scoped lang="scss" src="~/assets/css/page.scss">
</style>
