<template>
   <div class="slides">
        <img :src="list[index]" />
        <div class="btn-group">
            <slot :prev="prev" :next="next">
                <button @click="prev">&#8249;</button>
                <button @click="next">&#8250;</button>
            </slot>
        
        </div>
    </div>
</template>

<script setup>
import {defineProps,ref, onMounted,watch} from 'vue'

const props = defineProps({
  list: {
    tpye: Array,
    required: true,
    default: [],
  },
  timer: {
    tpye: Number,
    required: false,
    default: 3,
  },
  autoShow: {
    type: Boolean,
    required: false,
    default: false
  }
})

let index = ref(0)

onMounted(()=>{
    autoShow()
})

watch(index, (v) => {
    if(v > props.list.length-1) index.value = 0
})


function prev(){
    if(index.value >  0) index.value -=1
    else index.value = props.list.length-1
}

function next() {
    if(index.value < props.list.length-1) index.value +=1
    else index.value = 0 
}

function autoShow(){
    if(props.autoShow) {
        window.setInterval(() => {
        index.value += 1
      }, props.timer * 1000 );
    }
}
</script>

<style scoped>
    .slides{
        position: relative;
        box-shadow: 0px 0px 10px rgb(0 0 0 / 50%);
    }

    img{
        width: 50%;
        height: 300px;
        object-fit: contain;
    }

    .btn-group {
        width: 100%;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        display: flex;
        justify-content: space-between;
    }
</style>