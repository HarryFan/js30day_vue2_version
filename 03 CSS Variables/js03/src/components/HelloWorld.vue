<template>
  <div>
    <h2>Update CSS Variables with <span class='hl'>JS</span></h2>

    <div class="controls">
      <label for="spacing">Spacing:</label>
      <input id="spacing" type="range" name="spacing" min="10" max="200" v-model="spacing" data-sizing="px">

      <label for="blur">Blur:</label>
      <input id="blur" type="range" name="blur" min="0" max="25" v-model="blur" data-sizing="px">

      <label for="base">Base Color</label>
      <input id="base" type="color" name="base" v-model="base">
    </div>

    <img :style="imgStyle" src="https://source.unsplash.com/7bwQXzbF6KE/800x500">
  </div>
</template>
<style>
  :root {
    --base: #ffc600;
    --spacing: 10px;
    --blur: 10px;
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
    width: 100px;
  }
</style>



<script>
  export default {
    data() {
      return {
        base: '#ffc600',
        spacing: '10px',
        blur: '10px'
      }
    },
    computed: {
      imgStyle() {
        return {
          padding: this.spacing,
          background: this.base,
          filter: `blur(${this.blur})`
        }
      }
    }
  }
</script>