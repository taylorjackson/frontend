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
        <li><a href="${currentLink.url}" target="_blank">${currentLink.name}</a></li>
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
</script>


{#if ready}
  <header>
    <img id="logo" in:fade={{ duration: 1500 }} src="android-chrome-192x192.png" alt="Impossible Triangle"/>
    <h1 in:fly={{ y: 40, duration: 3000 }}>ContinuumDAO</h1>
  </header>
  <main>
    <a in:fade={{ delay: 1000, duration: 1000 }} href="groups.js" download>
      Download White Paper
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

  footer {
    width: 40%;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  }

  :global(li) {
    list-style-type: none;
    margin: 0;
    padding: 0;
  }

  :global(.link-icon) {
    width: 25px;
    height: 25px;
  }
</style>