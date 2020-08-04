<template>
  <div id="app">
    <Nav />
    <router-view/>
  </div>
</template>

<script>
import Nav from '@/components/Nav.vue'

export default {
  components: {
    Nav
  }
}
</script>



<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&family=Ubuntu+Mono:wght@700&display=swap');

:root {
  --cyan: #DEFFFC;
  --lavender: #E3E4F6;
  --pink: #E7C8DD;
  --d-pink: #DBAFC1;
  --black: #141414;
}

*, body {
  margin: 0;
  padding: 0;
  font-family: 'Roboto', sans-serif;
  color: var(--black);
}

h1, h2, h3, h4, h5, h6 {
  font-family: 'Ubuntu Mono', monospace;
}

#app {
  max-width: 1000px;
  margin: auto;
  padding: 0;
}

a {
  text-decoration: none;
}

</style>
