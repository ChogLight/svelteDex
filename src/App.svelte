<script>
    import { onMount } from "svelte"
    import Header from './components/Header.svelte'
    import Pokemon from "./components/Pokemon.svelte"
    import Card from "./components/Card.svelte"
    let counter = 0
    let url = `https://pokeapi.co/api/v2/pokemon?limit=21&offset=${counter}`
    let result
    let promise
    let pokemon = []
    
    onMount(async () => {
      const response = await fetch(url)
      promise = response.json()

    })
</script>

<main class="container mt-20 mx-auto">

    <Header/>

    <div class="md:grid grid-cols-3 gap-4 mt-20">
      {#await promise}
        <div>
          <h1>...waiting for info</h1>
        </div>
      {:then results}

      {#if results !== undefined}
        {#each results.results as pokemon }
        <Pokemon url = {pokemon.url}/>
        {/each}
      {/if}
      {:catch error}
      <div>error.message</div>
      {/await}
    </div>
    
    

</main>

