<script>
    import { onMount } from "svelte"
    import Header from './components/Header.svelte'
    import Pokemon from "./components/Pokemon.svelte"
    import Card from "./components/Card.svelte"
    let counter = 0
    let url = `https://pokeapi.co/api/v2/pokemon?limit=21&offset=${counter}`
    let pokemonArray = []
    let urlArray = []
    let card
    let pokemon

    export let setCard = (statement) => {
        card = statement
    }

    const setPokemon = (settedPokemon) => {
        pokemon = settedPokemon
    } 
    
    onMount(async () => {
        const res = await fetch(url)
        const result = await res.json()
        urlArray = result.results
        let pokeArray = []
    Promise.all(urlArray.map(url => {
      fetch(url.url)
      .then(response => response.json())
      .then(response => {
        pokeArray.push(response)
        pokeArray.sort((a,b) => {
          return a.id  - b.id
        })
        pokemonArray = [...pokeArray]
      })
    }))
    })

    console.log(urlArray)
    
</script>


<main class="container mt-20 mx-auto">

    <Header/>

    {#if (card)}
      <Card setCard = {setCard} pokemon = {pokemon}/>
      {console.log(card)}
    {/if}

    <div class="md:grid grid-cols-3 gap-4 mt-20">
      {#each pokemonArray  as pokemon }
        
        <Pokemon pokemon = {pokemon} setCard = {setCard} setPokemon = {setPokemon}/>
      {/each}
    </div>
    
    

</main>

