<template>
    <div>     
      <ul>
        <WatchItem v-for="item in watches"
        v-bind:watch="item"
        v-bind:key="item.id"        
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
        WatchItem
    },
    methods: {
    
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