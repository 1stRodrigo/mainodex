<script setup>
    const pokemon = defineProps([ "name", "urlBasePng" ])
</script>

<template>
    <div class="col-4 ">
        <div class="card mb-3 cardListPokemon">
            <p class="text-center">{{ pokemon.name }}</p>
            <img 
            :src="urlBasePng" 
            alt="..."
            height="90" 
            class="card-img-top p-2"/>
        </div>
    </div>
</template>

<style scoped>
    .cardListPokemon{
        background: radial-gradient(#ffe600, #c25f02b4);
        cursor: pointer;
    }
    .cardListPokemon:hover{
        
        background: radial-gradient(#ffe818, #c25f02);
    }
    .cardListPokemon img:hover{
        padding: .1rem;
    }

</style>