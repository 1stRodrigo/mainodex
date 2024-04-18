<script setup>
    import { onMounted, reactive, ref, computed } from 'vue';
    import ListPokemons from '../components/ListPokemons.vue';
    import CardPokemonSelected from '@/components/CardPokemonSelected.vue';
    
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
                    
                    <CardPokemonSelected/>

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