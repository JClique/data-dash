<template>
  <ul>
    <li>data-dash</li>
    <li class="nav-link"><router-link to="/">Home</router-link></li>
    <li class="nav-link"><router-link to="/about">About</router-link></li>
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
  top: 0;
  margin: auto;
  padding: 0;
  text-align: right;
  font-weight: 900;
}

li {
  padding: .5rem 1rem;
  margin: .5rem;
  border-radius: 10px;
  text-align: center;
  transition: .4s;
}

li.nav-link:hover {
  background-color: var(--cyan);
}

li:first-child {
  margin-right: auto;
  font-size: 1.4rem;
  font-weight: 100;
  font-family: 'Ubuntu Mono', monospace;
}

</style>
