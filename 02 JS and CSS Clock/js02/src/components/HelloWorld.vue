<template>
  <div class="clock">
    <div class="clock-face">
      <div class="hand hour-hand" :style="{ transform: `rotate(${hourDegrees}deg)` }"></div>
      <div class="hand min-hand" :style="{ transform: `rotate(${minsDegrees}deg)` }"></div>
      <div class="hand second-hand" :style="{ transform: `rotate(${secondsDegrees}deg)` }"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      secondsDegrees: 0,
      minsDegrees: 0,
      hourDegrees: 0,
    }
  },
  mounted() {
    this.setDate();
    setInterval(this.setDate, 1000);
  },
  methods: {
    setDate() {
      const now = new Date();

      const seconds = now.getSeconds();
      this.secondsDegrees = ((seconds / 60) * 360) + 90;

      const mins = now.getMinutes();
      this.minsDegrees = ((mins / 60) * 360) + ((seconds/60)*6) + 90;

      const hour = now.getHours();
      this.hourDegrees = ((hour / 12) * 360) + ((mins/60)*30) + 90;
    }
  }
}
</script>

<style scoped>
 html {
      background:#018DED url(http://unsplash.it/1500/1000?image=881&blur=50);
      background-size:cover;
      font-family:'helvetica neue';
      text-align: center;
      font-size: 10px;
    }

    body {
      margin: 0;
      font-size: 2rem;
      display:flex;
      flex:1;
      min-height: 100vh;
      align-items: center;
    }

    .clock {
      width: 30rem;
      height: 30rem;
      border:20px solid white;
      border-radius:50%;
      margin:50px auto;
      position: relative;
      padding:2rem;
      box-shadow:
        0 0 0 4px rgba(0,0,0,0.1),
        inset 0 0 0 3px #EFEFEF,
        inset 0 0 10px black,
        0 0 10px rgba(0,0,0,0.2);
    }

    .clock-face {
      position: relative;
      width: 100%;
      height: 100%;
      transform: translateY(-3px); /* account for the height of the clock hands */
    }

    .hand {
      width:50%;
      height:6px;
      background:black;
      position: absolute;
      top:50%;
      transform-origin: 100%;
      transform: rotate(90deg);
      transition: all 0.05s;
      transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
    }
</style>
