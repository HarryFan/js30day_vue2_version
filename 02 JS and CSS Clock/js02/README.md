
```markdown

# Vue 2 Clock Component



這是一個使用 Vue 2 製作的時鐘元件。它會顯示當前的時間，並且每秒更新一次。



## 使用方法



1. 將 `Clock.vue` 檔案放入你的 Vue 專案中。



2. 在你的父元件中引入 `Clock` 元件：



```javascript

import Clock from './path-to-your-components/Clock.vue'

```



3. 在你的父元件的 `components` 選項中註冊 `Clock` 元件：



```javascript

components: {

  Clock

}

```



4. 在你的父元件的模板中使用 `Clock` 元件：



```html

<clock></clock>

```



## 功能



- 顯示當前的時間

- 每秒自動更新



## 開發



這個元件使用 Vue 2 開發，並使用 Vue 的生命週期鉤子 `mounted` 來設定一個每秒執行一次的 `setInterval`，用於更新時鐘的角度。



## 風格



你可以在 `Clock.vue` 的 `<style>` 區塊中自定義你的 CSS 樣式。



## 貢獻



如果你有任何問題或建議，歡迎開 issue 或提交 pull request。

```

​

