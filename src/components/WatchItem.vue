<template>
    <li>
     Здесь будет секундомер {{ watch.time }}
    </li>
  </template>
  
  <script>

  export default {
    name:'WatchItem',
    props: ['watch'],
    filters: {
      
    }
  }
  </script>
  
  <style scoped>
    li {
      border: 1px solid #e71717;
      display: flex;
      justify-content: space-between;
      padding: .5rem 2rem;
      margin-bottom: 1rem;
    }
  

  </style>