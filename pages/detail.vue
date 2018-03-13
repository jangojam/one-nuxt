<template>
  <section class="container">
    <div class="detail">
      <div class="d-header">
        <i class="icon-back icon iconfont  i-back" @click="goBack"></i>
      </div>
      <div class="d-content">
          <p class="c-title">{{pageInfo.hp_title}}</p>
          <p class="c-author" >作者/{{pageInfo.hp_author}}</p>
          <p class="c-text" v-html="pageInfo.hp_content"></p>
      </div>
    </div>
  </section>
</template>

<script>
var axios = require('axios')

export default {
    data(){
        return{
            item_id:'',
            pageInfo:{}
        }
    },
  components: {
  },
  created () {
      this.getDetail(this.item_id)
  },
  asyncData (context) {
    return { item_id:context.query.item_id}
  },
  methods:{
      getDetail: function(item_id) {
          var _this = this
        axios({
          method:'get',
          url:'http://v3.wufazhuce.com:8000/api/essay/'+item_id+'?channel=wdj&source=summary&source_id=9261&version=4.0.2&uuid=ffffffff-a90e-706a-63f7-ccf973aae5ee&platform=android',
        })
          .then(function(res) {
              _this.pageInfo  = res.data.data
            console.log(res.data.data)  
        });
      },
      goBack: function() {
        this.$router.go(-1)
      }
  }
}
</script>

<style scoped lang="scss" src="~/assets/css/detail.scss">
</style>
