<template>
  <div class="contener">
    <ul>
      <WatchItem v-for="item in watches" v-bind:watch="item" v-bind:key="item.id" v-on:watch-stop="watchStop"
        v-on:watch-play="watchPlay" v-on:watch-pause="watchPause" />
      <AddWatch v-on:watch-create="createWatch" />
    </ul>
  </div>
</template>
  
<script>
import WatchItem from '@/components/WatchItem'
import AddWatch from "@/components/addWatch.vue";
export default {
  name: 'WatchList',
  props: ['watches'],
  components: {
    WatchItem,
    AddWatch
  },
  methods: {
    watchStop(id) {
      this.$emit('watch-stop', id)
    },
    watchPlay(id) {
      this.$emit('watch-play', id)
    },
    watchPause(id) {
      this.$emit('watch-pause', id)
    },
    createWatch(watch) {
      this.$emit('watch-create', watch)
    }
  }
}
</script>
  
<style scoped>
.contener {  
  padding: 72px 0px;
  display: flex;
  justify-content: center;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  gap: 50px;
  max-width: 875px;
  flex-wrap: wrap;
  justify-content: baseline;

}
@media (max-width: 900px) {
  ul {
  max-width: 600px; 
}
}
@media (max-width: 600px) {
  ul {
    max-width: 225px; 
}
}
</style>