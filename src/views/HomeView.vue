<script setup>
    import { onMounted, reactive } from 'vue';
    import ListPokemons from '../components/ListPokemons.vue';

    let pokemons = reactive();

    onMounted( ()=>{
        fetch("https://pokeapi.co/api/v2/pokemon?limit=150&offset=0")
        .then( res => res.json() )
        .then( res => pokemons = res.results );
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
                            <ListPokemons
                            v-for="pokemon in pokemons"
                            :key="pokemon.name"
                            :name="pokemon.name"
                            />
                        </div>
                    </div>
                </div>
            </div>
        
        </div>
    </main>
</template>