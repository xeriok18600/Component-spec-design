# component-spec-design

## 開發環境為: Vue 3

## 開發項目: 圖片輪播套件, 自動填入

## 圖片輪播套件

檔案位置: /component-spec-design/src/components/ImageSlideShow.vue

### Props

| Name | Type | Default | Description |
| :-----| ----: | :----: | :----:|
| list | Array | [ ] | 傳入要顯示的圖片陣列 |
| timer | Number | 3 | 單位為秒, 自動切換圖片的週期|
| autoShow | Boolean | false | 自動切換圖片|


### Slots

| Name | Description |
| :-----: | :----:|
| default | 可替換前後切換按鈕  |


### Examples
![FireShot Capture 046 - component-spec-design - localhost](https://user-images.githubusercontent.com/31687242/179689826-56ce9384-23bc-4303-ac5f-e1cd7e42bbd6.png)

```
<template>
  <h1>輪播套件</h1>
  <ImageSlideShow :list="list" >
  </ImageSlideshow>
</template>

<script>
import ImageSlideShow from './components/ImageSlideShow.vue'

export default {
  name: 'App',
  components: {
    ImageSlideShow
  },
  data(){
    return {
      list:['https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/1200px-Vue.js_Logo_2.svg.png',
            'https://asset-cdn.tecky.io/2022/04/02/logo-og_uid_62487e2fa3766.png',
            'https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Angular_full_color_logo.svg/1200px-Angular_full_color_logo.svg.png',]
    }
  }
}
</script>
```

#### Slots Sample
![FireShot Capture 048 - component-spec-design - localhost](https://user-images.githubusercontent.com/31687242/179696142-9f5ccf84-61ba-4aaf-95e6-84dc43fff074.png)
```
<template>
  <h1>輪播套件</h1>
  <ImageSlideShow :list="list" >
      <template #default="{ prev, next }">
        <button @click="prev">1</button>
        <button @click="next">2</button>
    </template>
  </ImageSlideshow>
</template>

<script>
import ImageSlideShow from './components/ImageSlideShow.vue'

export default {
  name: 'App',
  components: {
    ImageSlideShow
  },
  data(){
    return {
      list:['https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/1200px-Vue.js_Logo_2.svg.png',
            'https://asset-cdn.tecky.io/2022/04/02/logo-og_uid_62487e2fa3766.png',
            'https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Angular_full_color_logo.svg/1200px-Angular_full_color_logo.svg.png',]
    }
  }
}
</script>
```

---

## 自動填入

檔案位置: /component-spec-design/src/components/AutocompleteInput.vue

### Props

| Name | Type | Default | Description |
| :-----| ----: | :----: | :----:|
| list | Array | [ ] | 傳入要搜尋的資料 |
| value | String | '' | 輸入框的值|
| placeholder | String | '' | 輸入框顯示字|


### Slots

| Name | Description |
| :-----: | :----:|
| default | 可替換搜尋不符時顯示的文字  |


### Examples
![FireShot Capture 050 - component-spec-design - localhost](https://user-images.githubusercontent.com/31687242/179753880-8d249056-7cc7-4f9e-92c2-279c2d8ce43b.png)


```
<template>
  <h1>自動輸入 {{search}}</h1>
  <AutocompleteInput v-model="search" :list="filterList" :placeholder="'請輸入單字'"></AutocompleteInput>
  
</template>

<script>
import AutocompleteInput from './components/AutocompleteInput.vue'
export default {
  name: 'App',
  components: {
    AutocompleteInput
  },
  data(){
    return {
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

```

#### Slots Sample
![FireShot Capture 051 - component-spec-design - localhost](https://user-images.githubusercontent.com/31687242/179754503-04f71793-f692-467d-9a7e-3fc6182bc4e8.png)

```
<template>
  <h1>自動輸入 {{search}}</h1>
  <AutocompleteInput v-model="search" :list="filterList" :placeholder="'請輸入單字'">
     <h1>就是找不到</h1>
  </AutocompleteInput>
  
</template>

<script>
import AutocompleteInput from './components/AutocompleteInput.vue'
export default {
  name: 'App',
  components: {
    AutocompleteInput
  },
  data(){
    return {
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
```
