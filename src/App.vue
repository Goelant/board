<script setup lang="ts">
import { onMounted, onUpdated } from 'vue';
defineProps(
  {
    msg: {
    type: String,
    default: 'pyratt'
  }
})

onMounted(() => {
  console.log('updated')
  if (window.innerWidth < 650) {
    console.log(1-(0.2 + Math.exp(parseFloat(`0.`+window.innerWidth))))
    let top = document.getElementById('top');
    top ? top.style.scale = `${1-(1.9 - Math.exp(parseFloat(`0.`+window.innerWidth)))}` : null;
  }
});
</script>

<template>
  <div id="container">

    <div id="top">
      <div id="top-container">
        <h1 style='z-index: 1; top: 0px;'>pyratt</h1>
        <h1 style='z-index: 3; top: 90px;'>pyratt</h1>
        <h1 style='z-index: 2; top: 180px;'>pyratt</h1>
      </div>
      <img id='grid-image' src="./assets/grid.png" />
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
  box-shadow: 5px 5px rgb(6, 28, 1), 8px 8px rgb(6, 28, 1);
  cursor: pointer;
  transition: ease-out 0.2s;
  transform: scale(.8);
}

#top:hover {
  border: 4px solid rgb(6, 28, 1);
  box-shadow: 8px 8px rgb(6, 28, 1), 12px 12px rgb(6, 28, 1);
  transition: ease-out 0.2s;
}

#top h1,
#top #grid-image,
#top:hover h1 {
  transition: ease-out 0.2s;
  left: 0;
}

#top:hover h1:first-child {
  left: -250px !important;
}
#top:hover h1:last-child {
  left: 250px !important;
}
#top:hover #grid-image {
  transition: ease-out 0.2s;
  opacity: .75;
}

#top-container {
  position: relative;
  top: -32px;
}

#grid-image {
  width: 115%;
  transform: rotate(25deg) translateX(-8%) translateY(-20%);
  z-index: 0;
  opacity: .5;
  transition: ease-out 0.2s;
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