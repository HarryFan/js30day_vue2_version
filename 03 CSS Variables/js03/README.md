# 元件名稱：HelloWorld

  

## 屬性 (Props)

- \`msg\` (類型：String)：接收一個字串作為訊息內容。

  

## 資料 (Data)

- \`base\` (類型：String，預設值：'#ffc600')：代表基本顏色的數值。

- \`blur\` (類型：String，預設值：'10')：代表模糊程度的數值。

- \`spacing\` (類型：String，預設值：'10')：代表間距的數值。

  

## 方法 (Methods)

- \`handleUpdate(property: string)\`：處理 `<input>` 元素變動事件的方法。參數 \`property\` 是指要更新的屬性名稱。

  

## 生命週期鉤子 (Lifecycle Hooks)

- \`mounted()\`：在元件掛載完成後執行的生命週期鉤子。此時綁定事件監聽器，以處理 `<input>` 元素的變動事件。

  

## 範例

  

```html

<template>

  <div class="controls">

    <label for="spacing">Spacing:</label>

    <input id="spacing" type="range" name="spacing" min="10" max="200" v-model="spacing" @input="handleUpdate('spacing')" data-sizing="px">

  

    <label for="blur">Blur:</label>

    <input id="blur" type="range" name="blur" min="0" max="25" v-model="blur" @input="handleUpdate('blur')" data-sizing="px">

  

    <label for="base">Base Color</label>

    <input id="base" type="color" name="base" v-model="base" @input="handleUpdate('base')">

  </div>

</template>

  

<script>

export default {

  name: 'HelloWorld',

  props: {

    msg: String

  },

  data() {

    return {

      base: '#ffc600',

      blur: '10',

      spacing: '10'

    }

  },

  methods: {

    handleUpdate(property) {

      const value = this\[property\];

      const suffix = this.$el.querySelector(\`input\[name="${property}"\]\`).dataset.sizing || '';

      document.documentElement.style.setProperty(`--${property}`, value + suffix);

    }

  },

  mounted() {

    const inputs = this.$el.querySelectorAll('.controls input');

  

    inputs.forEach(input => input.addEventListener('change', this.handleUpdate));

    inputs.forEach(input => input.addEventListener('mousemove', this.handleUpdate));

  }

}

</script>

  

<style scoped>

:root {

  --base: #ffc600;

  --spacing: 10px;

  --blur: 10px;

}

  

img {

  padding: var(--spacing);

  background: var(--base);

  filter: blur(var(--blur));

}

  

.hl {

  color: var(--base);

}

  

body {

  text-align: center;

  background: #193549;

  color: white;

  font-family: 'helvetica neue', sans-serif;

  font-weight: 100;

  font-size: 50px;

}

  

.controls {

  margin-bottom: 50px;

}

  

input {

  width: 100