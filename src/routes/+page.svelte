<script>
  import { onMount } from "svelte"
  import { fade, fly } from "svelte/transition"
  import groups from "../groups"

  let ready = false

  onMount(() => {
    ready = true
  })

  let socials = ""

  for(let i = 0; i < groups.length; i++) {
    let currentSocialsList = ""
    const currentGroup = groups[i]

    for(let j = 0; j < groups[i].links.length; j++) {
      const currentLink = currentGroup.links[j]
      currentSocialsList = currentSocialsList.concat(`
        <a href="${currentLink.url}" target="_blank"><li>${currentLink.name} &#8599</li></a>
      `)
    }

    // <img class="link-icon" src="brand-assets/${currentLink.icon}"/>

    socials = socials.concat(`
      <ul>
        <h4>${currentGroup.title}</h4> 
        ${currentSocialsList}
      </ul>
    `)
  }

  const toggleDarkMode = () => {
    window.document.body.classList.toggle("dark-mode")
  }
</script>


{#if ready}
  <header>
    <img id="logo" in:fade={{ duration: 1500 }} src="android-chrome-192x192.png" alt="Impossible Triangle"/>
    <h1 in:fly={{ y: 40, duration: 3000 }}>ContinuumDAO</h1>
  </header>
  <main>
    <a in:fade={{ delay: 1000, duration: 1000 }} href="">
      <button id="download-white-paper" on:click={toggleDarkMode}>
        Download White Paper
      </button>
    </a>
  </main>
  <footer>
    {@html socials}
  </footer>
{/if}


<style>
  :global(body) {
    width: 100%;
    margin: 0;
    padding: 0;
    background-color: #fffefe;
    color: #444;
    transition: background-color 0.3s, color 0.3s;
  }

  :global(body.dark-mode) {
    background-color: #111010;
    color: #4d8fa1;
  }

  header {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0 auto;
    width: 100%;
  }

  #logo {
    width: 200px;
    height: 200px;
    margin: 20px 0;
  }

  h1 {
    margin: 0;
    padding: 0;
    font-size: 40px;
    letter-spacing: 5px;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  }

  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    margin: 150px auto;
  }

  :global(a) {
    text-decoration: none;
    color: inherit;
  }

  #download-white-paper {
    color: #174650;
    padding: 10px;
    font-weight: 600;
    border: none;
    border-radius: 10px;
    transition: 0.3s ease;
    background-color: aquamarine;
    cursor: pointer;
    opacity: 0.9;
  }

  #download-white-paper:hover {
    color: #174650;
    opacity: 1;
    box-shadow: 0 0 5px aquamarine;
  }

  footer {
    width: 50%;
    margin: 0 auto;
    padding: 0;
    display: flex;
    justify-content: space-between;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  }

  @media only screen and (max-width: 1000px) {
    footer {
      width: 100%;
      flex-direction: column;
      justify-content: normal;
      align-items: center;
    }
  }

  :global(ul) {
    min-width: 200px;
    list-style-type: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
  }

  :global(li) {
    list-style-type: none;
    width: 100px;
    margin: 0;
    padding: 10px;
    cursor: pointer;
  }
</style>