<template>
    <li>
        <div class="watch">
            <div class="contener">
                <div class="times" v-bind:class="{ times_inactive: (watch.active) }">
                    <div class="times__text-block" v-if="watch.hours>0">{{ (watch.hours > 9) ? watch.hours : '0' + watch.hours }}</div>
                    <div class="times__column" v-if="watch.hours>0">:</div>
                    <div class="times__text-block" v-if="(watch.minuts>0)||(watch.hours>0)">{{ (watch.minuts > 9) ? watch.minuts : '0' + watch.minuts }}</div>
                    <div class="times__column" v-if="(watch.minuts>0)||(watch.hours>0)">:</div>
                    <div class="times__text-block">{{ (watch.seconds > 9) ? watch.seconds : '0' + watch.seconds }}</div>
                </div>
            </div>

            <div class="contener buttons" v-bind:class="{ buttons_inactive: (watch.active) }">
                <button class="button button__play"  v-if="!watch.active" 
                    v-on:click="$emit('watch-play', watch.id)">
                    <svg width="17" height="20" viewBox="0 0 17 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M0 20V0L17 10L0 20Z" fill="#9E9E9E" />
                    </svg>
                </button>
                <button class="button button__pause" v-if="watch.active" v-on:click="$emit('watch-pause', watch.id)">
                    <svg width="10" height="20" viewBox="0 0 10 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <rect x="7" width="3" height="20" fill="#FFFFFF" />
                        <rect width="3" height="20" fill="#FFFFFF" />
                    </svg>
                </button>
                <button class="button button__stop" 
                    v-bind:class="{ button__stop_inactive: (watch.active) }" v-on:click="$emit('watch-stop', watch.id)">
                </button>
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
.times{
    display: flex;
    justify-content: center;
    align-items: center;
}
.times_inactive {
    color: var(--text-color-inactive);
}
.times__text-block{
    min-width: 3.2rem;
    text-align:center;
    
}
.times__column{
    padding: 1px;
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

.buttons_inactive {
    border-top: 1px solid var(--text-color-inactive);
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
    
}

.button__play, .button__pause {
    background-color: var(--block-backgound-color);
}

</style>