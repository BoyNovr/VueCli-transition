<template>
    <button class="btn btn-danger" @click="interupt=!interupt">
    Interupt  </button>
    <div v-if="interupt">
    <button class="btn btn-primary" @click="status=!status">
        button Toggle</button>
        <hr>
    <transition 
    mode="out-in" 
    name="custom"
    :css="false"
    enter-active-class="dog"
    leave-active-class="cat"
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter"
    @before-leave="beforeLeave"
    @leave="leave"
    @after-leave="afterLeave"
    @enter-cancelled="enterCancelled"
    @leave-cancelled="leaveCancelled"
    >
        <div class="p-3 mb-2 bg-danger text-white" v-if="!status">
            OFF
        </div>
        <div class="p-3 mb-2 bg-success text-white" v-else>
            ON
        </div>
    </transition>
   <hr>
   <button class="btn btn-primary" @click="library=!library">
    Button Library
    </button>
    <hr>
    <transition 
    name="custom-animation-width-animate-css"
    enter-active-class="animate__animated animate__fadeInRight"
    leave-active-class="animate__animated animate__fadeOutLeft">
        <div class="p-3 mb-2 bg-info text-white"
        v-if="library">
            Hello
        </div>
    </transition>
    </div>
</template>
<script>
import Velocity from 'velocity-animate';
export default{
    data(){
        return{
            status:false,
            library:false,
            interupt:true
        }
    },
    methods:{
        beforeEnter(el){
            el.style.opacity=0;
        },
        enter(el, done) {
            Velocity(el,{
                opacity:1, fontSize:'30px'
            },{
                duration:5000,
                complete:done
            })
        },
        afterEnter(){
            console.log('after enter')
        },
        beforeLeave(){
            console.log('before leave')
        },
        leave(el,done){
            Velocity(el,{
                opacity:0,
                rotateZ:'180deg'
            },{
                duration:2000,
                loop:2,
                complete:done
            })
        },
        afterLeave(){
            console.log('after leave')
        },
        enterCancelled(){
            console.log('enter cancelled')
        },
        leaveCancelled(){
            console.log('Leave Cancelled')
        }
    }
}
</script>
<style>

.custom-enter-from,
.custom-leave-to{
    opacity: 0;
}
.dog, 
.cat{
    transition: 1s;
}
.custom-enter-to, 
.custom-leave-from{
    opacity: 1;
}
</style>