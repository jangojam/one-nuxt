<template>
  <div> 
    <div class="i-header" >
        <i class="icon-category icon iconfont  i-cate" @click="showTab"></i>
    </div>
  </div>
</template>
<script>
  import '~/assets/iconfont/iconfont.css'
export default {
  methods: {
    showTab: function() {
      this.$emit('show')
      
    }
  }
}
</script>

<style scoped lang="scss"> 
.i-header{
    position: fixed;
    top: 0;
    left: 0;
    z-index: 100;
    width: 100%;
    height: 2.5rem;
    background: #00cc99;
    .i-cate{
        display: block;
        height: 100%;
        width: 4rem;
        text-align: center;
        font-size: 1.5rem;
        line-height: 2.5rem;
        color: #fff;
    }
}
</style>
