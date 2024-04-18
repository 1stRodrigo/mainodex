<script setup>
    /*===== IMPORT DOS "HOOKS" ===== */
    import { onMounted, reactive, ref, computed } from 'vue';

    /*===== IMPORT DAS ROTAS ===== */
    import ListPokemons from '../components/ListPokemons.vue';
    import CardPokemonSelected from '@/components/CardPokemonSelected.vue';
    
    let pokemons = reactive({ list: [] });
    let urlBasePng = ref('https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/home/shiny/')
    let searchPokemonField = ref("")
    let pokemonSelected = reactive(ref());

    
    onMounted( ()=>{
        fetch("https://pokeapi.co/api/v2/pokemon?limit=150&offset=0")
        .then( res => res.json() )
        .then( res => pokemons.value = res.results );
    })

    /*===== INICIO Barra de pesquisa dinâmica ===== */
    const pokemonsFiltered = computed(()=>{
        if(pokemons.value && searchPokemonField.value){
            return pokemons.value.filter(pokemon=>
            pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
            )
        }
        return pokemons.value;
    })
    /*===== FIM Barra de pesquisa dinâmica ===== */

    /* como está chamando a api, a função se torna "async" */
    const selectPokemon = async (pokemon) => {
        await fetch(pokemon.url)
        .then(res => res.json())
        .then(res => pokemonSelected.value = res);

        console.log(pokemonSelected.value)
        
    }

</script>

<template>
    <main>
        <div class="container">   
                     
            <div class="row mt-4">
                <div class="col-sm-12 col-md-6">
                    
                    <CardPokemonSelected
                    :name="pokemonSelected?.name"
                    :xp="pokemonSelected?.base_experience"
                    :height="pokemonSelected?.height"
                    :sprite="pokemonSelected?.sprites.other.home.front_shiny"
                    />
                </div>

                    <div class="col-sm-12 col-md-6">
                        <div class="card card-list">
                            <div class="card-body row">

                                <!-- Barra de pesquisa -->
                                <div class="mb-3">                                
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
                                </div>
                    

                                <ListPokemons
                                v-for="pokemon in pokemonsFiltered"
                                :key="pokemon.name"
                                :name="pokemon.name"
                                :urlBasePng="urlBasePng + pokemon.url.split('/')[6] + '.png'"
                                @click="selectPokemon(pokemon)"
                                />
                            </div>
                        </div>
                    </div>
            </div>
        
        </div>
    </main>
</template>

<style scoped>
.card-list{
    max-height: 450px;
    overflow-y: scroll;
    overflow-x: hidden;    
}
</style>