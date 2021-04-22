<template>
  <div>
    <Navbar />

    <Nuxt />
  </div>
</template>

<script>
import Navbar from "../components/Navbar"

export default {
  components: {
    Navbar,
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@300;700&display=swap');
html {
  font-family: 'Merriweather', serif;
  font-weight: 300;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.font-bold {
  font-weight: 700;
}
</style>
