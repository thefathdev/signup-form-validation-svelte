<script>
  import Copy from './lib/Copy.svelte'
  import Form from './lib/Form.svelte'
</script>

<main>
  <div class="container">
    <Copy />
    <Form />
  </div>
</main>

<style>
  main {
    min-height: 100vh;
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: var(--clr-red);
    background-image: url(./assets/images/bg-intro-mobile.png);
  }
  .container {
    max-width: 30rem;
    margin: 5em auto;
    display: flex;
    flex-direction: column;
    gap: 3em;
    padding-inline: 1.5em;
  }

  @media (min-width: 36rem) {
    .container {
      max-width: 74rem;
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      padding-inline: 2em;
      gap: 2.5em;
    }
  }
</style>
