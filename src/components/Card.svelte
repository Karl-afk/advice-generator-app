<script>
  import { onMount } from "svelte";
  let advice = {};
  let width;
  onMount(async () => {
    newAdvice();
  });
  async function newAdvice() {
    const res = await fetch("https://api.adviceslip.com/advice");
    const fullResponse = await res.json();
    advice = fullResponse.slip;
  }
</script>

<svelte:window bind:innerWidth={width} />
<div class="card">
  <div class="card_header">
    <p>advice #{advice.id}</p>
  </div>
  <div class="card_body">&ldquo;{advice.advice}&rdquo;</div>
  {#if width > 585}
    <!-- content here -->
    <svg width="444" height="16" xmlns="http://www.w3.org/2000/svg"
      ><g fill="none" fill-rule="evenodd"
        ><path fill="#4F5D74" d="M0 8h196v1H0zM248 8h196v1H248z" /><g
          transform="translate(212)"
          fill="#CEE3E9"
          ><rect width="6" height="16" rx="3" /><rect
            x="14"
            width="6"
            height="16"
            rx="3"
          /></g
        ></g
      ></svg
    >
  {:else}
    <!-- else content here -->
    <svg width="295" height="16" xmlns="http://www.w3.org/2000/svg"
      ><g fill="none" fill-rule="evenodd"
        ><path fill="#4F5D74" d="M0 8h122v1H0zM173 8h122v1H173z" /><g
          transform="translate(138)"
          fill="#CEE3E9"
          ><rect width="6" height="16" rx="3" /><rect
            x="14"
            width="6"
            height="16"
            rx="3"
          /></g
        ></g
      ></svg
    >
  {/if}
  <button type="submit" on:click={() => newAdvice()}
    ><svg width="24" height="24" xmlns="http://www.w3.org/2000/svg"
      ><path
        d="M20 0H4a4.005 4.005 0 0 0-4 4v16a4.005 4.005 0 0 0 4 4h16a4.005 4.005 0 0 0 4-4V4a4.005 4.005 0 0 0-4-4ZM7.5 18a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Z"
        fill="#202733"
      /></svg
    ></button
  >
</div>

<style>
  .card {
    background-color: hsl(217, 19%, 24%);
    width: 460px;
    height: fit-content;
    color: #fff;
    border-radius: 15px;
    padding: 16px 48px 0px 48px;
    text-align: center;
    position: relative;
  }
  .card_header {
    color: hsl(150, 100%, 66%);
    text-transform: uppercase;
    font-size: 12px;
    letter-spacing: 3px;
  }
  .card_body {
    font-size: 28px;
    margin: 24px 0 38px 0;
  }
  .card > svg {
    position: relative;
    bottom: 5px;
  }
  button {
    background-color: hsl(150, 100%, 66%);
    border: none;
    padding: 16px;
    border-radius: 50%;
    position: relative;
    top: 27px;
    left: 0px;
    cursor: pointer;
  }
  button:link {
    box-shadow: none;
  }
  button:visited {
    box-shadow: none;
  }
  button:hover {
    box-shadow: 0 0 50px 1px hsl(150, 100%, 66%);
  }
  button:active {
    box-shadow: none;
  }

  button svg {
    position: relative;
    left: 0;
    top: 2px;
  }
  @media screen and (max-width: 585px) {
    .card {
      width: 340px;
      padding: 24px 20px 0 20px;
    }
  }
  @media screen and (max-width: 400px) {
    .card {
      width: 280px;
    }
    .card > svg {
      left: -6px;
    }
  }
</style>
