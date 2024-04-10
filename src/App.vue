<script setup lang="ts">
import { onMounted } from 'vue';
defineProps(
  {
    msg: {
    type: String,
    default: 'pyratt'
  }
})

onMounted(() => {
  console.log('coucou')
  let h1 = document.querySelectorAll('h1');
  h1.forEach((element:HTMLElement, index) => {
      console.log(index)
      element.style.top=90*index + 'px'
  })
})

</script>

<template>
  <div id="container">

    <div id="top">
      <div id="top-container">
        <h1 style='z-index: 0;'>pyratt</h1>
        <h1 style='z-index: 2;'>pyratt</h1>
        <h1 style='z-index: 1;'>pyratt</h1>
      </div>
    </div>

  <div id="right">
    <div id="clippers">
    </div>
    
  </div>

</div>
</template>

<style>
@font-face {
  font-family: "Antology";
  src:
    url("./assets/fonts/titles/antology/Antology.ttf") format("truetype");
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
  background: url('./assets/bg.jpeg') repeat;
  background-size: contain;
  top: 0;
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
}

#top {
  position: absolute;
  top: 2vw;
  width: 805px;
  height: 200px;
  border-radius: 16px;
  border: 4px solid rgb(6, 28, 1);
  overflow: hidden;
  box-shadow: 6px 6px rgb(6, 28, 1), 10px 10px rgb(6, 28, 1);
}

#top-container {
  position: relative;
  top: -32px;
}

h1 {
  color: var(--accent);
  font-size: 17rem;
  font-family: 'Antology', serif;
  margin: 0;
  position: absolute;
  line-height: 7rem;
  text-shadow: 2px 2px 1px rgb(238, 230, 201), -2px -2px 1px white;
}
</style>