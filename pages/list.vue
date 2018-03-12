<template>
  <div>
      <Tabs v-show="showTab" v-on:close="closeTab"></Tabs>
      <nuxt-child/>
  </div>
</template>

<script>
// import Tabs from "~/components/tabs.vue"
// export default{
//     data(){
//         return {
//             showTab: true
//         }
//     },
//     components: {
//         Tabs
//     },
//     methods:{
        
//     }
// }
</script>
<script>
import Tabs from "~/components/tabs.vue"
export default {
  data(){
    return{
        showTab: true
    }
  },
  components: {
    Tabs
  },
  methods: {
        closeTab: function () {  
            console.log(11)
            this.showTab = false
        }
  }
}
</script>