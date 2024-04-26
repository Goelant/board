<script setup lang="ts">
import { ref, onMounted } from 'vue';
import './assets/scripts/twitch-embed-v1.js';
let matrixCopied = ref(false)

function redirect(url:URL, type: string) {
  window.open(url, type)
}

function matrixCopy(content:string) {
  matrixCopied.value = true
  navigator.clipboard.writeText(content);
  setTimeout(() => {
    matrixCopied.value = false;
  }, 1500);
}

onMounted(() => {
  console.log('updated')
  if (window.innerWidth < 650) {
    console.log(1-(0.2 + Math.exp(parseFloat(`0.`+window.innerWidth))))
    let top = document.getElementById('top');
    top ? top.style.scale = `${1-(1.9 - Math.exp(parseFloat(`0.`+window.innerWidth)))}` : null;
  }

  var s = document.createElement("script");
  s.type = "text/javascript";
  s.src = "https://embed.twitch.tv/embed/v1.js";
  document.body.appendChild(s);

  new Twitch.Embed("twitch-embed", {
      width: 854,
      height: 480,
      channel: "lakavelive",
      // Only needed if this page is going to be embedded on other websites
      parent: ["embed.example.com", "othersite.example.com"]
    });
});
</script>

<template>
  <div id="container">
    <div id="bg1"></div>
    <div id="bg2"></div>
    <svg id="bg3" xmlns="http://www.w3.org/2000/svg" version="1.1" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:svgjs="http://svgjs.dev/svgjs" viewBox="0 0 2000 2000" width="2000" height="2000"><defs><filter id="nnnoise-filter" x="-20%" y="-20%" width="140%" height="140%" filterUnits="objectBoundingBox" primitiveUnits="userSpaceOnUse" color-interpolation-filters="linearRGB">
      <feTurbulence type="fractalNoise" baseFrequency="0.102" numOctaves="4" seed="15" stitchTiles="stitch" x="0%" y="0%" width="100%" height="100%" result="turbulence"></feTurbulence>
      <feSpecularLighting surfaceScale="15" specularConstant="0.75" specularExponent="20" lighting-color="#202124" x="0%" y="0%" width="100%" height="100%" in="turbulence" result="specularLighting">
            <feDistantLight azimuth="3" elevation="100"></feDistantLight>
        </feSpecularLighting>
      <feColorMatrix type="saturate" values="0" x="0%" y="0%" width="100%" height="100%" in="specularLighting" result="colormatrix"></feColorMatrix>
      </filter></defs><rect width="2000" height="2000" fill="transparent"></rect><rect width="2000" height="2000" fill="#202124" filter="url(#nnnoise-filter)"></rect>
    </svg>

    <RouterLink tag="div" to="/" id="top" >
      <div id="top-container">
        <h1 style='z-index: 1; top: 0px;'>pyratt</h1>
        <h1 style='z-index: 3; top: 90px;'>pyratt</h1>
        <h1 style='z-index: 2; top: 180px;'>pyratt</h1>
      </div>
      <img id='grid-image' src="./assets/grid.png" />
    </RouterLink>

  <div id="left">
    <div id="twitch-container">
      <div id="twitch" >
        <iframe
            id='twitch-iframe'
            src="https://player.twitch.tv/?channel=lakavelive&parent=localhost&muted=true"
            allowfullscreen>
        </iframe>
      </div>
    </div>
    <div id="dots">
      <div id='grid-image-bg'></div>
      <div id="github" @click="redirect('https://github.com/Goelant', 'blank')">
        <svg xmlns="http://www.w3.org/2000/svg" height="1em" fill="currentColor" viewBox="0 0 512 512">
          <path
            d="M 171.3548387096774 407.741935483871 Q 170.32258064516128 411.8709677419355 166.19354838709677 411.8709677419355 Q 160 411.8709677419355 160 407.741935483871 Q 161.03225806451613 404.64516129032256 165.16129032258064 404.64516129032256 Q 170.32258064516128 404.64516129032256 171.3548387096774 407.741935483871 L 171.3548387096774 407.741935483871 Z M 139.3548387096774 403.61290322580646 Q 138.32258064516128 406.7096774193548 143.48387096774192 408.7741935483871 Q 148.6451612903226 409.80645161290323 149.67741935483872 406.7096774193548 Q 150.70967741935485 402.5806451612903 145.5483870967742 401.5483870967742 Q 140.38709677419354 400.51612903225805 139.3548387096774 403.61290322580646 L 139.3548387096774 403.61290322580646 Z M 184.7741935483871 401.5483870967742 Q 179.61290322580646 402.5806451612903 179.61290322580646 406.7096774193548 Q 180.6451612903226 409.80645161290323 185.80645161290323 409.80645161290323 Q 190.96774193548387 407.741935483871 190.96774193548387 404.64516129032256 Q 189.93548387096774 401.5483870967742 184.7741935483871 401.5483870967742 L 184.7741935483871 401.5483870967742 Z M 252.90322580645162 6.193548387096774 Q 142.4516129032258 8.258064516129032 72.25806451612904 78.45161290322581 L 72.25806451612904 78.45161290322581 L 72.25806451612904 78.45161290322581 Q 2.064516129032258 148.6451612903226 0 258.06451612903226 Q 1.032258064516129 345.80645161290323 48.516129032258064 411.8709677419355 Q 96 477.93548387096774 175.48387096774192 504.7741935483871 Q 194.06451612903226 505.80645161290323 193.03225806451613 492.38709677419354 Q 193.03225806451613 488.258064516129 193.03225806451613 476.9032258064516 Q 193.03225806451613 453.16129032258067 193.03225806451613 429.4193548387097 Q 190.96774193548387 429.4193548387097 173.41935483870967 431.48387096774195 Q 154.83870967741936 432.51612903225805 134.19354838709677 427.35483870967744 Q 113.54838709677419 421.16129032258067 105.29032258064517 398.4516129032258 Q 105.29032258064517 396.38709677419354 97.03225806451613 381.93548387096774 Q 88.7741935483871 368.51612903225805 76.38709677419355 360.258064516129 Q 74.3225806451613 359.2258064516129 68.12903225806451 352 Q 60.903225806451616 345.80645161290323 78.45161290322581 344.7741935483871 Q 79.48387096774194 343.741935483871 92.90322580645162 348.9032258064516 Q 106.3225806451613 353.03225806451616 117.6774193548387 371.61290322580646 Q 136.25806451612902 399.48387096774195 157.93548387096774 399.48387096774195 Q 180.6451612903226 399.48387096774195 193.03225806451613 393.2903225806452 Q 197.16129032258064 368.51612903225805 209.5483870967742 358.19354838709677 Q 164.1290322580645 356.1290322580645 130.06451612903226 335.48387096774195 Q 96 315.8709677419355 93.93548387096774 243.61290322580646 Q 93.93548387096774 222.96774193548387 100.12903225806451 209.5483870967742 Q 105.29032258064517 196.1290322580645 117.6774193548387 183.74193548387098 Q 115.61290322580645 177.5483870967742 113.54838709677419 158.96774193548387 Q 111.48387096774194 140.38709677419354 120.7741935483871 113.54838709677419 Q 139.3548387096774 110.45161290322581 164.1290322580645 124.90322580645162 Q 189.93548387096774 138.32258064516128 192 141.41935483870967 Q 192 141.41935483870967 192 141.41935483870967 Q 222.96774193548387 132.1290322580645 257.03225806451616 132.1290322580645 Q 290.06451612903226 132.1290322580645 322.06451612903226 141.41935483870967 Q 322.06451612903226 140.38709677419354 335.48387096774195 132.1290322580645 Q 347.8709677419355 123.87096774193549 364.38709677419354 117.6774193548387 Q 380.9032258064516 110.45161290322581 393.2903225806452 113.54838709677419 Q 402.5806451612903 140.38709677419354 400.51612903225805 158.96774193548387 Q 398.4516129032258 177.5483870967742 395.35483870967744 183.74193548387098 Q 407.741935483871 196.1290322580645 414.96774193548384 209.5483870967742 Q 422.19354838709677 222.96774193548387 422.19354838709677 243.61290322580646 Q 421.16129032258067 293.16129032258067 404.64516129032256 316.9032258064516 Q 387.0967741935484 339.61290322580646 360.258064516129 347.8709677419355 Q 333.4193548387097 356.1290322580645 303.48387096774195 358.19354838709677 Q 320 369.5483870967742 321.03225806451616 405.6774193548387 Q 321.03225806451616 443.8709677419355 321.03225806451616 473.80645161290323 Q 321.03225806451616 487.2258064516129 321.03225806451616 492.38709677419354 Q 320 505.80645161290323 338.5806451612903 504.7741935483871 Q 417.03225806451616 477.93548387096774 464.51612903225805 411.8709677419355 Q 510.96774193548384 345.80645161290323 512 258.06451612903226 Q 510.96774193548384 185.80645161290323 476.9032258064516 129.03225806451613 Q 441.80645161290323 72.25806451612904 384 39.225806451612904 Q 325.16129032258067 7.225806451612903 252.90322580645162 6.193548387096774 L 252.90322580645162 6.193548387096774 Z M 100.12903225806451 362.3225806451613 Q 98.06451612903226 364.38709677419354 101.16129032258064 367.48387096774195 Q 104.25806451612904 370.5806451612903 106.3225806451613 368.51612903225805 Q 108.38709677419355 366.4516129032258 105.29032258064517 363.35483870967744 Q 103.2258064516129 360.258064516129 100.12903225806451 362.3225806451613 L 100.12903225806451 362.3225806451613 Z M 88.7741935483871 354.06451612903226 Q 88.7741935483871 356.1290322580645 91.87096774193549 358.19354838709677 Q 94.96774193548387 359.2258064516129 96 357.16129032258067 Q 97.03225806451613 355.0967741935484 93.93548387096774 353.03225806451616 Q 90.83870967741936 352 88.7741935483871 354.06451612903226 L 88.7741935483871 354.06451612903226 Z M 122.83870967741936 390.19354838709677 Q 120.7741935483871 393.2903225806452 123.87096774193549 397.4193548387097 Q 128 400.51612903225805 131.09677419354838 398.4516129032258 Q 132.1290322580645 395.35483870967744 129.03225806451613 391.2258064516129 Q 124.90322580645162 388.1290322580645 122.83870967741936 390.19354838709677 L 122.83870967741936 390.19354838709677 Z M 110.45161290322581 375.741935483871 Q 108.38709677419355 377.80645161290323 110.45161290322581 381.93548387096774 Q 113.54838709677419 385.03225806451616 116.64516129032258 384 Q 118.70967741935483 381.93548387096774 116.64516129032258 377.80645161290323 Q 113.54838709677419 373.6774193548387 110.45161290322581 375.741935483871 L 110.45161290322581 375.741935483871 Z"
          />
        </svg>
      </div>
      <div id="matrix" :class='{copied: matrixCopied }' @click="matrixCopy('@rouge-gorge:matrix.org')">
        <!-- m icon by Free Icons (https://free-icons.github.io/free-icons/) -->
        <svg v-if='!matrixCopied' xmlns="http://www.w3.org/2000/svg" height="1em" fill="currentColor" viewBox="0 0 512 512">
          <path
            d="M 28.31858407079646 5.663716814159292 Q 53.23893805309734 0 69.09734513274336 20.38938053097345 L 256 301.30973451327435 L 256 301.30973451327435 L 442.9026548672566 20.38938053097345 L 442.9026548672566 20.38938053097345 Q 458.76106194690266 0 483.6814159292035 5.663716814159292 Q 508.60176991150445 14.725663716814159 509.7345132743363 40.7787610619469 L 509.7345132743363 475.75221238938053 L 509.7345132743363 475.75221238938053 Q 509.7345132743363 491.6106194690266 499.53982300884957 501.8053097345133 Q 489.34513274336285 512 473.4867256637168 512 Q 457.62831858407077 512 447.43362831858406 501.8053097345133 Q 437.23893805309734 491.6106194690266 437.23893805309734 475.75221238938053 L 437.23893805309734 160.8495575221239 L 437.23893805309734 160.8495575221239 L 286.5840707964602 387.39823008849555 L 286.5840707964602 387.39823008849555 Q 275.2566371681416 403.2566371681416 256 403.2566371681416 Q 236.7433628318584 403.2566371681416 225.41592920353983 387.39823008849555 L 74.76106194690266 160.8495575221239 L 74.76106194690266 160.8495575221239 L 74.76106194690266 475.75221238938053 L 74.76106194690266 475.75221238938053 Q 74.76106194690266 491.6106194690266 64.56637168141593 501.8053097345133 Q 54.3716814159292 512 38.51327433628319 512 Q 22.654867256637168 512 12.460176991150442 501.8053097345133 Q 2.265486725663717 491.6106194690266 2.265486725663717 475.75221238938053 L 2.265486725663717 40.7787610619469 L 2.265486725663717 40.7787610619469 Q 3.398230088495575 14.725663716814159 28.31858407079646 5.663716814159292 L 28.31858407079646 5.663716814159292 Z"
          />
        </svg>
        <span v-else id='matrix-text'>Copié !</span>
      </div>
      <div id="dot3"></div>
      <div id="dot4"></div>
    </div>
  </div>

  <div id="right">
    <div id="clipper1" @click="redirect('https://twitter.com/pyratt_', 'blank')">
      <h2>TWITTER</h2>
      <div class='clipper-image-twitter'></div>
      <div id='grid-image-bg'></div>
    </div>
    <!-- <div id="clipper2" @click="redirect('https://instagram.com/pyratt.sh', 'blank')">
      <h2>INSTAGRAM</h2>
      <div id='grid-image-bg'></div>
    </div> -->
    <div id="clipper3" @click="redirect('https://lakave.live', 'blank')">
      <h2>LAKAVELIVE</h2>
      <div class='clipper-image-lakavelive'></div>
      <div id='grid-image-bg'></div>
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
@font-face {
  font-family: "Godiaz";
  src:
    url("./assets/fonts/titles/godiaz/Godiaz.ttf") format("truetype");
}

:root {
  --white: #dadbd6;
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
* {
  font-family: 'Godiaz', serif;
}

#container {
  width:100vw;
  height: 100vh;
  top: 0;
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}

#bg1 {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: -1;
  background: url('./assets/bg.jpeg') repeat;
  background-size: contain;
}

#bg2 {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: -1;
  background: url('./assets/bg.jpeg') repeat;
  background-size: contain;
  transform: rotate(30deg);
}

#bg3 {
  position: absolute;
}

.c-te__chat{
  display: none !important;
}

#top {
  position: absolute;
  width: 805px;
  height: 200px;
  border-radius: 16px;
  border: 4px solid var(--dark);
  overflow: hidden;
  box-shadow: 5px 5px var(--dark), 8px 8px var(--dark);
  cursor: pointer;
  transition: ease-out 0.2s;
  transform: scale(.8) translateY(-13%);
  z-index: 2; 
  top: 4vh; 
}

#top:hover {
  border: 4px solid var(--dark);
  box-shadow: 8px 8px var(--dark), 12px 12px var(--dark);
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
#top:hover h1:nth-child(2) {
  color: rgb(6, 28, 1)  !important;
}

/* Position du pyratt à l'interieur */
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
}

h2 {
  color: var(--accent);
  font-family: 'Godiaz', serif;
  font-size: 80px;
  margin-top: 0;
  top: -23px;
  left: 10px;
  position: absolute;
}

#left,
#right {
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  position: relative;
  top: calc(5vh + 200px);
  border-top: 10px solid var(--dark);
}

#left {
  width: 50vw;
  max-width: 600px !important;
  border-right: 10px solid var(--dark);
}

.copied {
  width: 150px !important;
  background-color: var(--white) !important;
  color: var(--dark) !important;;
  transition: ease-out 0.2s !important;;
}

.opacity-invisible {
  opacity: 0;
}
.opacity-visible {
  opacity: 1;
}

#twitch-container {
  background-color: var(--dark);
  position: relative;
  width: 100%;
}

#twitch {
  aspect-ratio: 16/9;
  position: relative;
  width: 100%;
  border-top-right-radius: 16px;
  overflow: hidden;
}

#twitch:after {
  content: "" !important;
  position: absolute;
  display: block !important;
  width: 16px !important;
  height: 16px !important;
  pointer-events: none !important;
  clip-path: inset(0);
  border-bottom-right-radius: 16px !important;
  transform: rotate(270deg) !important;
  box-shadow: 0 0 0 18px var(--dark) !important;
  top: 0;
  right: 0;
  z-index: 1;
}
#twitch:before {
  content: "" !important;
  position: absolute;
  display: block !important;
  width: 16px !important;
  height: 16px !important;
  pointer-events: none !important;
  clip-path: inset(0);
  border-bottom-right-radius: 16px !important;
  transform: rotate(0deg) !important;
  box-shadow: 0 0 0 18px var(--dark) !important;
  bottom: 0;
  right: 0;
  z-index: 1;
}


#twitch-iframe {
  position: relative;
  width: 100%;
  height: 100%;
  border: none;
}

#dots {
  width: 100%;
  height: 65px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  border-top: 10px solid var(--dark);
  border-bottom: 10px solid var(--dark);
  position: relative;
  overflow: hidden;
}

#dots #grid-image-bg {
  top: 25px;
}

#dots:after {
  content: "" !important;
  position: absolute;
  display: block !important;
  width: 16px !important;
  height: 16px !important;
  pointer-events: none !important;
  clip-path: inset(0);
  border-bottom-right-radius: 16px !important;
  transform: rotate(270deg) !important;
  box-shadow: 0 0 0 18px var(--dark) !important;
  top: 0;
  right: 0;
  z-index: 1;
}

#dots:before {
  content: "" !important;
  position: absolute;
  display: block !important;
  width: 16px !important;
  height: 16px !important;
  pointer-events: none !important;
  clip-path: inset(0);
  border-bottom-right-radius: 16px !important;
  transform: rotate(0deg) !important;
  box-shadow: 0 0 0 18px var(--dark) !important;
  bottom: 0;
  right: 0;
  z-index: 1;
}

#dots > div:not(#grid-image-bg) {
  border-radius: 50px;
  width: 40px;
  height: 40px;
  background-color: var(--dark);
  color: var(--white);
  transition: ease-out 0.2s;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

#dots > div:hover:not(#grid-image-bg) {
  background-color: var(--white);
  color: var(--dark);
  transition: ease-out 0.2s;
}

#dots svg {
  width: 22px;
  height: 22px;
}

#matrix-text {
  font-size: 30px !important;
  text-wrap: stable;
  white-space: nowrap;
}

#right {
  flex-grow: 1;
}

#right > div {
  width: 100%;
  height: 65px;
  border-bottom: 4px solid var(--dark);
  box-shadow: 0px 5px var(--dark), 0px 6px var(--dark);
  transition: ease-out 0.2s;
  margin-bottom: 6px;
  cursor: pointer;
  overflow: hidden;
  position: relative;
}

#right > div:hover {
  height: 300px;
  transition: ease-out 0.2s;
}

#right > div:after {
  content: "" !important;
  position: absolute;
  display: block !important;
  width: 16px !important;
  height: 16px !important;
  pointer-events: none !important;
  clip-path: inset(0);
  border-bottom-right-radius: 16px !important;
  transform: rotate(90deg) !important;
  box-shadow: 0 0 0 18px var(--dark) !important;
  bottom: 0;
  left: 0;
  z-index: 1;
}
#right > div:before {
  content: "" !important;
  position: absolute;
  display: block !important;
  width: 16px !important;
  height: 16px !important;
  pointer-events: none !important;
  clip-path: inset(0);
  border-bottom-right-radius: 16px !important;
  transform: rotate(180deg) !important;
  box-shadow: 0 0 0 18px var(--dark) !important;
  top: 0;
  left: 0;
  z-index: 1;
}

#grid-image-bg {
  position: absolute;
  width: 2000px;
  height: 2000px;
  background: url('./assets/grid.png') repeat;
  transform: rotate(30deg) translate(-50%, -50%);
  opacity: .5;
  z-index: -1;
}

</style>