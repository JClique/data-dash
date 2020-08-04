<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
  </div>
</template>

<script>
export default {
  name: 'About',
}
</script>

<style scoped>
  .about {
    margin: 1rem;
    padding: 1rem;
  }

  .about h1 {
    margin-bottom: 1rem;
    padding: .25rem;
    border-radius: 5px;
    background-color: var(--lavender);
  }
</style>
