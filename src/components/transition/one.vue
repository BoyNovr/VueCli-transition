<template>
<transition>
    <div
    class="p-3 mb-2 bg-success text-white" v-if="display"
    >
    Hello   
    </div>
    
</transition>
    <button class="btn btn-primary" @click="display=!display">
    Change Display</button>
<hr>
<transition>
    <div 
    class="p-3 mb-2 bg-warning text-white"
    v-if="display2"
    >
    Hello   
    </div>
    
</transition>
    <button class="btn btn-primary" @click="display2=!display2">
    Change Display</button>
<hr>


<transition name="slide">
    <div 
    class="p-3 mb-2 bg-warning text-white"
    v-if="display3"
    >
    Hello   
    </div>
</transition>
    <button class="btn btn-primary" @click="display4=!display4">
    Change Display</button>
<hr>
<transition name="slideUp">
    <div 
    class="p-3 mb-2 bg-warning text-white"
    v-if="display4"
    >
    Hello   
    </div>
    
</transition>
    <button class="btn btn-primary" @click="display4=!display4">
    Change Display</button>

</template>
<script>
export default{
    data(){
        return{
            display:false,
            display2:false,
            display3:false,
            display4:false
        }
    }
}
</script>

<style>
.v-enter-from,.v-leave-to{
    opacity: 0;
}
.v-enter-active, .v-leave-active{
    transition: 1s;
}
.v-enter-to, .v-leave-from{
    opacity: 1;
}
.slide-enter-from{
    transform: translateX(190px);
    opacity: 0;
}
.slide-enter-active{
    transition: all 1s ease;
}
.slide-enter-to{
    opacity: 1;
}
.slide-leave-from{
    opacity: 1;
    background-color: red !important;
}
.slide-leave-active{
    transition: all 1s ease-in;
}
.slide-leave-to{
    opacity: 0;
    background-color: black !important;
    transform: translateX(100px);
}
/* ======================== */

.slideUp-enter-active{
    animation: slideUp 1s ease-in-out;
}
.slideUp-leave-active{
    animation: slideDown 5s ease-in-out;
}
@keyframes slideUp{
    from{
        opacity: 0;
        transform: translateY(15px);
    }to{
        opacity: 1;
        transform: translateY(0px);
    }
}
@keyframes slideDown{
    from{
        opacity: 1;
        transform: translateY(0px);
    }to{
        opacity: 0;
        transform: translateY(15px);
    }
}


</style>