<script setup>
/* Lógica do scroll infinito*/
    
    import { ref } from 'vue';
    import ListPokemons from './ListPokemons.vue';

    const listEl = ref(null)
    const pokemonsToShow = 15;
    const pokemonsList = ref(await getPokemons(pokemonsToShow, 0));
    
/* Lógica da lista dos pokemons*/
</script>

<template>
    <div>
        <ul ref="listEl">
            <li v-for="pokemons in pokemonsList">
                
            </li>
        </ul>
    </div>
</template>

<style scoped>
ul {
    background-color: #ffe600;
    list-style: none;
    max-height: 600px;
    width: 600px;
    overflow: scroll;
    padding: 12px 20px;
}

</style>
