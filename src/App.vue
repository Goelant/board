<script setup lang="ts">
import clippers from './components/clippers.vue';
defineProps(
  {
    msg: {
    type: String,
    default: 'pyratt'
  }
})
</script>

<template>
  <div id="container">

    <div id="left">
      <h1>pyratt</h1>
    </div>

  <div id="right">
    <div id="clippers">
      <clippers src="@/../clippers/twitter/index.html" link="https://twitter.com/pyratt_" height='1000' width='600'  transform="rotate(-0.01turn) scale(0.8)" />
      <clippers src="@/../clippers/mastodon/index.html" link="https://pyratt.social" height='400' width='700' transform="rotate(-0.02turn) scale(0.8)" left="300px"/>
      <clippers src="@/../clippers/twitch/index.html"  link="https://lakave.live/tv" height='500' width='800' transform="rotate(0.03turn) scale(0.8)" left="280px"/>
    </div>
    
  </div>

</div>
</template>

<style>
@font-face {
  font-family: "SketchG";
  src:
    url("./assets/fonts/titles/sketch_gothic_school/Sketch Gothic School.ttf") format("truetype");
}

:root {
  --dark: #202124;
  --accent: #496E3A;
}

body {
  background-repeat: repeat;
  background-size: contain;
  overflow: hidden;
}
</style>
<style scoped>
#container {
  width:100vw;
  height: 100vh;
  background: url('./assets/bg.jpeg');
  top: 0;
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
}
#left {
  padding: 12px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  width: 38vw;
  height: 100vh;
}
#right {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
h1 {
  color: var(--accent);
  font-size: 10rem;
  font-family: 'SketchG', serif;
  margin: 0;
  line-height: 14rem;
}
#clippers {
  transform: scale(0.8);
}
#bg {
  position: absolute;
  top: -50px;
}
#bg {
  display: inline-block;
}
</style>