<template>
  <div id="app">
    <WatchList v-bind:watches="watches" @watch-stop="watchStop" @watch-toggle="toggleWatch"/>
    <AddWatch @watch-create="createWatch"/>
  </div>
</template>

<script>
import WatchList from "@/components/WatchList";
import AddWatch from "@/components/addWatch.vue";

const startWatch=(watch)=>{
  watch.seconds++;
  if (watch.seconds>59){
    watch.minuts++;
    watch.seconds=0
  }
  if (watch.minuts>59){
    watch.hours++;
    watch.minuts=0
  }

}
export default {
  name: "App",
  data() {
    return {
      watches: [
        { id: 1, seconds:0, minuts:0, hours:0, isPlay:true, active: true, interval:undefined },
        { id: 2, seconds:53, minuts:59, hours:0, isPlay:true, active: true, interval:undefined  },
      ],
    };
  },
  components: {
    WatchList,
    AddWatch
  },
  methods: {
    watchStop: function (id) {
      const watch = this.watches.find((item) => {       
        return item.id === id;
      });     
      watch.active=false;
      clearInterval(watch.interval);
    },
    createWatch:function(watch){
        this.watches.push(watch)
    },
    toggleWatch: function (id) {
      const watch = this.watches.find((item) => {       
        return item.id === id;
      }); 
     
      watch.interval=setInterval(()=>startWatch(watch),1000);
      
    }

  },
};
</script>

<style>
@import "./assets/css/variables.css";
@import "./assets/css/global.css";

#app {
  padding: 72px 0;
  margin: 0 auto;
}
</style>
