<template>
  <!-- <h1>輪播套件</h1> -->
  <!-- <ImageSlideShow :list="list" >
  </ImageSlideshow> -->
  <h1>自動輸入 {{search}}</h1>
  <AutocompleteInput v-model="search" :list="filterList" :placeholder="'請輸入單字'">
    <h1>就是找不到</h1>
  </AutocompleteInput>
  
</template>

<script>
// import ImageSlideShow from './components/ImageSlideShow.vue'
import AutocompleteInput from './components/AutocompleteInput.vue'
export default {
  name: 'App',
  components: {
    // ImageSlideShow
    AutocompleteInput
  },
  data(){
    return {
      list:['https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/1200px-Vue.js_Logo_2.svg.png',
            'https://asset-cdn.tecky.io/2022/04/02/logo-og_uid_62487e2fa3766.png',
            'https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Angular_full_color_logo.svg/1200px-Angular_full_color_logo.svg.png'
            ],
      search: '',
      filterList: ['Apple','Book','Cat']
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

 button {
        background: rgba(0,0,0,.3);
        color: #ffffff;
        border:0;
        outline: none;
        cursor: pointer;
        width: 50px;
        height: 50px;
        font-size: 30px;
    }
</style>
