<template>
<div id="app"> 
  <WatchList v-bind:watches="watches"/>
</div>
</template>

<script>

import WatchList from '@/components/WatchList'
export default {
  name: 'App',
  data(){
    return {
      watches:[{id:1, time: 10, play:true},{id:2, time: 20, play:false}]
    }
  },
  components: {
    WatchList,
  }
}
</script>

<style >
@import './assets/css/variables.css';
@import './assets/css/global.css';
#app {  
 padding: 72px 0; 
 margin: 0 auto;
 
}
</style>
