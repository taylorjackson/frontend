<script>
  import { onMount } from "svelte"
  import { fade, fly } from "svelte/transition"

  let ready = false
  onMount(() => ready = true)
</script>


{#if ready}
  <header>
    <img in:fade={{ duration: 1500 }} src="cotinuum.png" alt="Impossible Triangle"/>
    <h1 in:fly={{ y: 40, duration: 3000 }}>ContinuumDAO</h1>
  </header>
  <main>
    <a in:fade={{ delay: 1000, duration: 1000 }} href="http://localhost:5173" target="_blank">White Paper Coming Soon</a>
  </main>
{/if}


<style>
  :global(body) {
    width: 100%;
    margin: 0;
    padding: 0;
    /*background-color: #fffefe;*/
    background-color: #000;
  }

  header {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0 auto;
    width: 100%;
  }

  img {
    width: 200px;
    height: 200px;
    margin: 20px 0;
  }

  h1 {
    margin: 0;
    padding: 0;
    font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    font-size: 40px;
    color: #444;
    letter-spacing: 5px;
  }

  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    margin: 150px auto;
  }

  a {
    text-decoration: none;
    color: royalblue;
    padding: 10px;
    border-radius: 10px;
    font-weight: 600;
    outline: 2px solid royalblue;
  }

  a:hover {
    background-color: aquamarine;
    transition: 0.5s ease;
  }
</style>
