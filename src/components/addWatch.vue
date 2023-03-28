<template>
 <li>
    <div class="watch">            
            <button class="button button__add" @click="createWath">
                <svg class="ico1" width="4" height="20" viewBox="0 0 4 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <rect width="4" height="20" fill="#E5E5E5" />
                    <rect width="1200" height="439" transform="translate(-598 -287)" fill="#353638" />
                    <rect x="-111" y="-50" width="225" height="120" fill="#696969" />
                    <rect x="0.5" width="3" height="20" fill="#9E9E9E" />
                    <rect x="-8" y="11.5" width="3" height="20" transform="rotate(-90 -8 11.5)" fill="#9E9E9E" />

                </svg>
                <svg class="ico2" width="20" height="4" viewBox="0 0 20 4" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <rect width="20" height="4" fill="#E5E5E5" />
                    <rect width="1200" height="439" transform="translate(-590 -295)" fill="#353638" />
                    <rect x="-103" y="-58" width="225" height="120" fill="#696969" />
                    <rect x="8.5" y="-8" width="3" height="20" fill="#9E9E9E" />
                    <rect y="3.5" width="3" height="20" transform="rotate(-90 0 3.5)" fill="#9E9E9E" />
                </svg>
            </button>       
    </div>
 </li>      
 
</template>
  
<script>

export default {
    name: 'AddWatch',
    props: [''],
    methods:{
        createWath (){            
            const newWatch={
                id: Date.now(),
                isPlay:true,
                seconds:0,
                minuts:0, 
                hours:0,
                active: false,
            }            
            this.$emit('watch-create', newWatch)
        }
    }

}
</script>
  
<style scoped>
.watch {
    width: 225px;
    height: 120px;
    background-color: var(--block-backgound-color);
    display: flex;
    justify-content: center;
    align-items: center;
}
.button {
    width: 20px;
    height: 20px;
    border: none;
    cursor: pointer;
    background-color: var(--block-backgound-color);    
    position: relative;
}
.ico1{
    position: absolute;
    bottom: 0px;
    left:8px;
}
.ico2{
    position: absolute;
    right:0px;
    top:8px
    
}
</style>