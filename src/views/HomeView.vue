<script setup>
    import { onMounted, reactive, ref, computed } from 'vue';
    import ListPokemons from '../components/ListPokemons.vue';
    
    let pokemons = reactive({ list: [] });
    let urlBasePng = ref('https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/home/shiny/')
    let searchPokemonField = ref("")

    
    onMounted( ()=>{
        fetch("https://pokeapi.co/api/v2/pokemon?limit=150&offset=0")
        .then( res => res.json() )
        .then( res => pokemons.value = res.results );
    })
    
    const pokemonsFiltered = computed(()=>{
        if(pokemons.value && searchPokemonField.value){
            return pokemons.value.filter(pokemon=>
            pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
            )
        }
        return pokemons.value;
    })

</script>

<template>
    <main>
        <div class="container">
            
            <div class="row mt-4">
                <div class="col-sm-12 col-md-6">

                    <!-- Card -->
                    <!--
                    <div class="card" style="width: 18rem;">
                        <img src="https://img.pokemondb.net/sprites/home/normal/bulbasaur.png" alt="Bulbasaur">
                    <div class="card-body">
                        <h5 class="card-title">Bulbassauro (RECEBER VIA API)</h5>
                        <p class="card-text">Bulbasaur é um pequeno Pokémon anfíbio, principalmente turquesa, com olhos vermelhos e um bulbo verde nas costas.(UTILIZAR API PARA DESCRIÇÃO)</p>
                        <a href="#" class="btn btn-primary">Mais detalhes</a>
                    </div>
                    </div>-->
                    
                    

                </div>

                <div class="col-sm-12 col-md-6">
                    <div class="card">
                        <div class="card-body row">

                            <div class="mb-3">                                
                                <!-- Barra de pesquisa -->
                                <label
                                    hidden
                                    for="searchPokemonField"
                                    class="form-label">
                                </label>

                                <input
                                v-model="searchPokemonField"
                                type="text" 
                                class="form-control" 
                                id="searchPokemonField"
                                placeholder="Buscar pokemón"
                                >
                                
                                <div class="dropdown me-1 mt-1">
                                    <button type="button" class="btn btn-secondary dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false" data-bs-offset="10,20">
                                    Filtrar
                                    </button>
                                    <ul class="dropdown-menu">
                                        <li class="nav-item dropdown">
                                            <a class="dropdown-item dropdown-toggle" href="#">Another action</a>
                                            <ul class="dropdown-menu">
                                                <li><a class="dropdown-item" href="#">Action</a></li>
                                                <li><a class="dropdown-item" href="#">Another action</a></li>
                                                <li><a class="dropdown-item" href="#">Something else here</a></li>
                                            </ul>
                                        </li>
                                        <li><a class="dropdown-item" href="#">Something else here</a></li>
                                    </ul>
                                </div>
                            </div>


                            <ListPokemons
                            v-for="pokemon in pokemonsFiltered"
                            :key="pokemon.name"
                            :name="pokemon.name"
                            :urlBasePng="urlBasePng + pokemon.url.split('/')[6] + '.png'"
                            />
                        </div>
                    </div>
                </div>
            </div>
        
        </div>
    </main>
</template>