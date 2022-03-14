<script>
  import Card from "./components/Card.svelte";
</script>

<main>
  <Card />
  <div class="attribution">
    Challenge by <a
      href="https://www.frontendmentor.io?ref=challenge"
      target="_blank">Frontend Mentor</a
    >. Coded by <a href="https://www.karlweinmueller.de">Karl Weinmüller</a>.
  </div>
</main>

<style>
  main {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 40px;
  }
  .attribution {
    font-size: 11px;
    text-align: center;
    color: #fff;
  }
  .attribution a {
    color: hsl(227, 100%, 88%);
  }
</style>
