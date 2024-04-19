<script setup>
    const pokemon = defineProps(["name", "xp", "height", "sprite", "loading"])
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
        </div>
    </div>
</template>


<style scoped>
.CardPokemonSelected{
    height: 75vh;
    background: radial-gradient(#ffe600, #b16501);
}
</style>