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
  overflow-x: hidden;
}

a {
  text-decoration: none;
}

button {
  background-color: var(--cyan);
  font-size: 1.2rem;
  font-family: 'Ubuntu Mono', monospace;
  padding: .5rem 1rem;
  border-radius: 10px;
  outline: none;
  border: none;
  appearance: none;
  margin: .5rem;
}

button:hover {
  outline: 2px dashed var(--d-pink);
  outline-offset: 2px;
}

button:active {
  background-color: var(--pink);
}
</style>
