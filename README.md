# component-spec-design

## 開發環境為: Vue 3

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
