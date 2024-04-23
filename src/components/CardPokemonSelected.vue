<script setup>
    const pokemon = defineProps(["name", "xp", "height", "sprite", "loading", "moves", "game_indices" ])
</script>

<template>
    <div 
    class="card CardPokemonSelected"
    :class="loading ? '' : 'animate__animated animate__flipInY'"
    >
    
        <img 
        v-if="pokemon.name"
        :alt="pokemon.name"
        :src="pokemon.sprite" 
        class="card-img-top pt-2" 
        height="250">

        <img
        v-else="pokemon.name"
        alt="???"
        src="../assets/img/Pokemon_Egg_icon-icons.com_67525.svg" 
        class="card-img-top pt-2" 
        height="250">
        
        <div class="card-body">
            
            <h5 class="card-title text-center">{{ pokemon.name || '???' }}</h5>
            <div class="row">
                <hr>
                <section class="col">
                    <strong>XP:</strong>
                    <span>{{ pokemon.xp }}</span>
                </section>
                
                <section class="col">
                    <strong>Altura:</strong>
                    <span>{{pokemon.height}}</span>
                </section>
            </div>
            <div class="row">
                <section class="col">
                    <strong>Movimentos de ataque:</strong>
                    <span>{{pokemon.moves}}</span>
                </section>
                
                <section class="col">
                    <strong>Tipo:</strong>
                    <span>{{}}</span>
                </section>
            </div>
            <div class="row">
                <section class="col">
                    <strong>Evoluções:</strong>
                    <span>{{}}</span>
                </section>
                
                <section class="col">
                    <strong>Game Indices:</strong>
                    <span>{{pokemon.game_indices}}</span>
                </section>

            </div>
        </div>
    </div>
</template>


<style scoped>
.CardPokemonSelected{
    height: 75vh;
    background: radial-gradient(#ffe600, #b16501);
}
</style>