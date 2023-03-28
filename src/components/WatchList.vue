<template>
    <div>     
      <ul >
        <WatchItem v-for="item in watches"
        v-bind:watch="item"
        v-bind:key="item.id"         
        v-on:watch-stop="watchStop"
        v-on:watch-toggle="watchToggle"            
        />
       
      </ul>
    </div>
  </template>
  
  <script>
  import WatchItem from '@/components/WatchItem'
 
  export default {
    name:'WatchList',
    props: ['watches'],
    components: {
        WatchItem,        
    },
  methods:{
    watchStop(id){
      this.$emit('watch-stop', id)
    },
    watchToggle(id){
      this.$emit('watch-toggle', id)
    }
  }
  }
  </script>
  
  <style scoped>


    ul {
      list-style: none;
      margin: 0;
      padding: 0;
    }
  </style>