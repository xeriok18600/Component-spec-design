<template>
  <div class="container">
    <input  type="text" v-model="searchValue" :placeholder="placeholder">
    <ul v-if="filterResults.isOpen" class="list-group">
        <li v-for="item in filterResults.lists" :key="item" class="list-group-item" @click="selectItem(item)">
          {{ item }}
        </li>
    </ul>
    <slot v-if="filterResults.noResult">
      <span>查無資料</span>
    </slot>
  </div>
  
</template>

<script setup>
import {defineProps, watch,reactive,defineEmits,computed} from 'vue'

const filterResults = reactive({ isOpen:false,lists: [], noResult: false})

const props = defineProps({
  list: {
    tpye: Array,
    required: true,
    default: [],
  },
  modelValue: {
    type: String,
    required: true,
    default: '',
  },
  placeholder: {
    type: String,
    required: false,
    default: '請輸入',
  }
})

const emit = defineEmits(['update:modelValue'])

const searchValue = computed({ 
    get: () => props.modelValue, 
    set: (v) => emit('update:modelValue', v) 
}) 

watch(searchValue, (v) => {
    filterList(v)
})

function filterList(v){
    filterResults.lists = props.list.filter((item)=>{
        return item.toLowerCase().indexOf(v.toLowerCase()) > -1;
    })
    filterResults.isOpen = props.modelValue.length > 0 && filterResults.lists.length > 0;
    filterResults.noResult = props.modelValue.length > 0 && filterResults.lists.length === 0;
}

function selectItem(v) {
  searchValue.value = v
  filterResults.isOpen = false
}

</script>

<style scoped>

.container {
  width: 300px;
  margin: auto;
}

ul {
  width: 100%;
  padding-left: 0;
  margin-top: 0;
  border-left: 1px solid;
  border-right: 1px solid;

}

li {
  list-style: none;
  text-align: left;
  border-bottom: 1px solid;
  padding: 5px;
  font-size: 14px;
  cursor: pointer;
}

input {
  width:100%;
  padding: 10px 5px;
}
</style>