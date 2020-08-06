<template>
  <ul>
    <li>data-dash</li>
    <li class="nav-link"><router-link to="/">Home</router-link></li>
    <li class="nav-link"><router-link to="/about">About</router-link></li>
    <li class="nav-link"><a href="https://github.com/JClique/data-dash">GitHub</a></li>
  </ul>
</template>

<script>
export default {
  name: 'Nav',

}
</script>

<style scoped>
ul {
  display: flex;
  justify-content: flex-start;
  list-style: none;
  max-width: 800px;
  margin: auto;
  margin-top: 1rem;
  padding: 0;
  text-align: right;
  font-weight: 900;
}

li {
  padding: .5rem;
  margin: .25rem;
  border-radius: 10px;
  text-align: center;
  transition: .4s;
}

li, a {
  font-size: 1.4rem;
  font-weight: 100;
  font-family: 'Ubuntu Mono', monospace;
}

li.nav-link:hover a {
  color: var(--pink);
  transition: .2s;
}

li:first-child {
  margin-right: auto;
  border: 3px dashed var(--lavender);
  border-radius: 0;
  white-space: nowrap;
}

</style>
