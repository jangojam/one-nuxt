<template>
  <div>
      <Tabs v-show="isShowTab" v-on:close="closeTab"></Tabs>
      <Header v-on:show="showTab"></Header>  
      <nuxt-child/>
  </div>
</template>

<script>
import Tabs from "~/components/tabs.vue"
import Header from "~/components/header.vue"
export default {
  data(){
    return{
        isShowTab: false
    }
  },
  components: {
    Tabs,
    Header
  },
  methods: {
        closeTab: function () {  
            console.log(11)
            this.isShowTab = false
        },
        showTab:function(){
          this.isShowTab = true
        }
  }
}
</script>