<script setup>
    const pokemon = defineProps(["name", "xp", "height", "sprite"])
</script>

<template>
    <div class="card CardPokemonSelected">
        <img 
            :alt="pokemon.name"
            :src="pokemon.sprite" 
            class="card-img-top pt-2" 
            height="250"
            
            >
        <div class="card-body">
            
            <h5 class="card-title text-center">{{ pokemon.name }}</h5>
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
    height: 450px;
    background: radial-gradient(#17bd5c, #074986);
}
</style>