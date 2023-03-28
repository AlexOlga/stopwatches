<template>
    <li>
        <div class="watch">
            <div class="contener">
                <div class="times" v-bind:class="{times_inactive: (!watch.active) }">
                    <span class="times__text">{{ (watch.hours>9)? watch.hours : '0'+ watch.hours }}</span>
                    <span class="times__text">:</span>
                    <span class="times__text">{{ (watch.minuts>9)? watch.minuts : '0'+ watch.minuts }}</span>
                    <span class="times__text">:</span>
                    <span class="times__text">{{ (watch.seconds>9)? watch.seconds : '0'+ watch.seconds }}</span>
                </div>
            </div>
            <div class="contener buttons"  v-bind:class="{buttons_inactive: (!watch.active) }">
                <button class="button button__play" v-bind:class="{button__play_inactive: (!watch.active)}"  v-bind:disabled="!watch.active" v-on:click="$emit('watch-toggle', watch.id)">
                    <svg width="17" height="20" viewBox="0 0 17 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M0 20V0L17 10L0 20Z" fill="#9E9E9E" />
                    </svg>
                </button>
                <button  class="button button__stop" v-bind:disabled="!watch.active" v-bind:class="{button__stop_inactive: (!watch.active) }" v-on:click="$emit('watch-stop', watch.id)" > </button>
            </div>
        </div>
    </li>
</template>
  
<script>
 

export default {
    name: 'WatchItem',
    props: ['watch'],  
    methods: {
       
    }
   
}


</script>
  
<style scoped>
li {

    border: 1px solid #e71717;
}

.watch {
    width: 225px;
    height: 120px;
    background-color: var(--block-backgound-color);
}

.times_inactive {
    color: var(--text-color-inactive);
}

.contener {
    padding: 2rem 0;
    display: flex;
    justify-content: center;
}

.buttons {
    gap: 4.8rem;
    border-top: 1px solid var(--text-color);
}
.buttons_inactive{
    border-top: 1px solid  var(--text-color-inactive);
}
.button {
    width: 20px;
    height: 20px;
    border: none;
    cursor: pointer;
}


.button__stop {
    background-color: var(--text-color);
     
}
.button__stop_inactive {
    background-color: var(--text-color-inactive);
    cursor: not-allowed;  
}

.button__play{
    background-color: var(--block-backgound-color);    
}
.button__play_inactive {
    cursor: not-allowed;  
}
</style>