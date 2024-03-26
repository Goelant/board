<script setup lang="ts">
defineProps(
  {
    src: {
      type: String,
      default: '',
      required: true
    },
    title: {
      type: String,
      default: '',
    },
    height: {
      type: String,
      default: '',
      required: true
    },
    width: {
      type: String,
      default: '',
      required: true
    },
    scrolling: {
      type: String,
      default: '',
    },
    transform: {
      type: String,
      default: '',
    },
    link: {
      type: String,
      default: '',
    },
    left: {
      type: String,
      default: '0'
    }
  }
)
</script>

<template>
  <router-link class="hover" to="link" :style="{
      width: parseInt(width) - 19 + 'px',
      height: parseInt(height) + 'px',
      transform: transform,
      left: left
      }">
    <div class='container'>

        <iframe 
        :src='src'
          :title='title'
          :height="height"
          :width="width"
          :scrolling="scrolling"
        ></iframe>
      <div class="background"></div>
      </div>
    </router-link>

</template>

<style scoped>
router-link {
  display: inline-block;
}
.container {
  overflow: hidden;
  border: solid 8px var(--dark);
  border-radius: 16px;
  padding: 0;
  background-color: var(--dark);
  z-index: 0;
  cursor: pointer;
  position: relative;
  display: inline-block;
}

.hover {
  cursor: pointer;
  z-index: -1;
  transform: scale(1);
  background-color: transparent;
  transition: transform 1s, z-index 0.3s step-start;
  position: relative;
}

.hover::after,
.container::after {
  display: inline-block;
}

.hover:hover {
  z-index: 1;
  transform: scale(1);
  transition: transform 1s, z-index 0.3s step-start;
}

.hover > .container > .background {
  background-color: transparent;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1000;
}

.hover:hover > .container > .background {
  transition: background-color 0.3s, transform 1s, z-index 0.3s step-start;
  animation: unblack 1.2s;
}

@keyframes unblack {
  from {
    background-color: var(--dark);
  }
  to {
    background-color: transparent;
  }
}



iframe {
  position: relative;
  top: -2px;
  left: -2px;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  height: 100vh;
  background-color: powderblue;
}
body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

</style>
