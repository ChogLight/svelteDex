<script>
    export let pokemon
    let card
    export let setCard

    
</script>



<div class="relative z-10" role="dialog" >
 
    <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>

    <div class="fixed inset-0 z-10 overflow-y-auto">
        <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
        
        <div class=" animate-appear relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all md:my-8 my-auto md:w-full md:max-w-lg">
            <div class="flex bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
                <div class="w-1/3 font-bold text-red-600 text-xs">
                <p class="font-bold text-red-600 text-lg">
                    N.°{pokemon.id}
                </p>
                <img class = "object-contain h-48 w-48"
                    src = {pokemon.sprites.other['official-artwork'].front_default} alt = "">
                </div>
                <div class="w-2/3">

                    <p class="font-bold mb-3 text-gray-700 uppercase">
                        Pokemon: {''}
                        <span class="font-normal capitalize">
                            {pokemon.name}
                        </span> 
                    </p>

                    <p class="font-bold mb-3 text-gray-700 uppercase">
                        Type: {''}
                        <span class="font-normal capitalize">
                        {pokemon.types[1]  ? `${pokemon.types[0].type.name}/${pokemon.types[1].type.name}` : pokemon.types[0].type.name}
                        </span>

                    </p>

                    <p class="font-bold mb-3 text-gray-700 uppercase">
                        Size: {''}
                        <span class="font-normal normal-case">
                        {`${pokemon.height/10}m`}
                        </span>

                    </p>
                    <p class="font-bold mb-3 text-gray-700 uppercase">
                        Weight: {''}
                        <span class="font-normal normal-case">
                        {`${pokemon.weight/10}Kg`}
                        </span>

                    </p>
                    <p class="font-bold mb-3 text-gray-700 uppercase">
                        Abilities: {''}
                        <span class="font-normal capitalize">    
                            {
                                pokemon.abilities.map((ability)=>{
                                    let {name, url} = ability
                                    console.log(name)
                                })        
                            }
                               
                        </span>
                    </p>
                    
                   

                </div>
                
            </div>
            <button 
                type = "button" 
                class="px-3 py-2 bg-red-500 m-5 text-white text-sm font-bold rounded-md"
                on:click={()=>setCard(false)}>
                Close
            </button>
        </div>
        </div>
    </div>
</div>