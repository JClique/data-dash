<template lang="html">
  <div class="box btn-box">
    <h2>{{ title }}</h2>

    <div class="box-content">
      <button type="button" name="button" @click="$emit('randomiseData')">
        <small> - Click for - </small>
          Random Data
      </button>
      <p>Generate randomised data to see chart transitions and animations.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "BarChart",
  props: ["title"],
}
</script>

<style lang="css" scoped>

.box.btn-box {
  background-color: transparent;
  padding: 0;
  margin: 0 1rem;
}

.box.btn-box p {
  padding: 1rem;
  font-size: .75rem;
}

.box-content {
  padding: 1rem;
  text-align: center;
  background-color: var(--cyan);
  border-radius: 5px;
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

h2 span {
  font-family: 'Ubuntu Mono', monospace;
  font-size: 0.9rem;
  color: white;
}

button {
  background-color: transparent;
  color: var(--d-pink);
  font-size: 1.5rem;
  font-family: 'Ubuntu Mono', monospace;
  padding: .5rem 1rem;
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
  color: white;
}

button small {
  display: block;
  font-size: .85rem;
  font-family: 'Ubuntu Mono', monospace;
  color: var(--d-pink);
}

button:active small {
  color: white;
}
</style>
