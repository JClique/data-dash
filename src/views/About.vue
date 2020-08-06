<template>
  <div class="about">
    <h1>what is data-dash?</h1>
    <p><b>'data-dash'</b> is a simple front-end application experimenting with data visualisation.
      It was written using Vue JS by developer <a href="https://github.com/JClique">J_Clique</a>,
      who after spending years moving data around with Python decided to finally learn a real Front-End framework.
    </p>
    <p>The inspiration for this project (and some of the first code!) was found in a video 'Data Visualisation with Vue JS' by Callum Macrae -
      <a href="https://www.youtube.com/watch?v=30v9xnB-GEo">here</a>
    </p>
    <p> The full source-code for this project can be found on GitHub - <a href="https://github.com/JClique/data-dash">here</a> </p>
  </div>
</template>

<script>
export default {
  name: 'About',
}
</script>

<style scoped>
  .about {
    padding: 1rem;
    max-width: 600px;
    margin: auto;
  }

  .about p {
    padding-bottom: 1rem;
  }

  .about b {
    font-family: 'Ubuntu Mono', monospace;
  }

  a {
    font-weight: bold;
    transition: 0;
  }

  a:hover {
    color: var(--pink);
  }

</style>
