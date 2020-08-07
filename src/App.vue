<template>
  <div id="app">
    <Nav />
    <transition name="router">
      <router-view/>
    </transition>
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
  --cyan: #DEFAF8;
  --lavender: #C8C9E6;
  --pink: #E7C8DD;
  --d-pink: #DBAFC1;
  --black: #141414;
}

* {  /* firefox scrollbar */
  scrollbar-width: thin;
  scrollbar-color: #C8C9E6 transparent;
}

::-webkit-scrollbar {
  width: 5px;
  height: 5px;
}

::-webkit-scrollbar-track {
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background: var(--lavender);
  border-radius: 5px;
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
  padding-bottom: 3rem;
}

a {
  text-decoration: none;
}

h1, h2 {
  display: block;
  margin: 1rem 0;
  padding: .25rem 1rem;
  border-radius: 5px;
  background-color: var(--lavender);
  color: white;
  text-align: center;
}

.router-enter-active, .router-leave-active {
  transition: opacity .5s ease-in-out, transform .5s ease;
}

.router-enter-active {
  transition-delay: .5s;
}

.router-enter, .router-leave-to {
  opacity: 0;
  transform: translateX(-100px);
}

.router-enter-to, .router-leave {
  opacity: 1;
  transform: translateX(0px);
}

</style>
