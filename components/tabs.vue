<template>
<div> 

    <div class="mask" @click='close'></div>
    <div class="tab">
      <i class="t-img"></i>
      <p class="t-name">jango</p>
      <p class="t-id">ID:12374</p>
      <nuxt-link :to="{name:'list'}"><p class="t-btn">首页</p></nuxt-link>
      <nuxt-link :to="{name:'list-read'}"><p class="t-btn">阅读</p></nuxt-link>
      <nuxt-link :to="{name:'list-music'}"><p class="t-btn">音乐</p></nuxt-link>
      <nuxt-link :to="{name:'list-movie'}"><p class="t-btn">影视</p></nuxt-link>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    close: function() {
      this.$emit('close')
      
    }
  }
}
</script>

<style scoped src="~/assets/css/tabs.scss" lang="scss"> 
</style>
