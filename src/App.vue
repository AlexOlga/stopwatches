<template>
  <div id="app">
    <WatchList v-bind:watches="watches" @watch-stop="watchStop" @watch-play="watchPlay" @watch-pause="watchPause" @watch-create="createWatch" />
       
  </div>
</template>

<script>
import WatchList from "@/components/WatchList";

const startWatch = (watch) => {
  watch.seconds++;
  if (watch.seconds > 59) {
    watch.minuts++;
    watch.seconds = 0
  }
  if (watch.minuts > 59) {
    watch.hours++;
    watch.minuts = 0
  }

}
export default {
  name: "App",
  data() {
    return {
      watches: [
        { id: 1, seconds: 40, minuts: 2, hours: 0, active: false, interval: undefined },
        { id: 2, seconds: 32, minuts: 25, hours: 0, active: false, interval: undefined },
        { id: 3, seconds: 15, minuts: 30, hours: 1, active: false, interval: undefined },
        { id: 4, seconds: 33, minuts: 20, hours: 1, active: false, interval: undefined },
      ],
    };
  },
  components: {
    WatchList,
       
  },
  methods: {
    watchStop: function (id) {
      const watch = this.watches.find((item) => {
        return item.id === id;
      });
      watch.active = false;
      clearInterval(watch.interval);
      watch.seconds = 0;
      watch.minuts = 0;
      watch.hours = 0;

    },
    createWatch: function (watch) {
      this.watches.push(watch)
    },
    watchPlay: function (id) {
      const watch = this.watches.find((item) => {
        return item.id === id;
      });
      watch.active = true;
      watch.interval = setInterval(() => startWatch(watch), 1000);

    },
    watchPause: function (id) {
      const watch = this.watches.find((item) => {
        return item.id === id;
      });
      watch.active = false;
      clearInterval(watch.interval);
    }

  },
};
</script>

<style>
@import "./assets/css/variables.css";
@import "./assets/css/global.css";


</style>
