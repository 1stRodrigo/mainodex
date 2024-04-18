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
        /*background: radial-gradient(#156f99, #0a2e50);*/
        background: linear-gradient(217deg, rgba(30, 255, 0, 0.377), rgba(255,0,0,0) 40%),
                    linear-gradient(127deg, rgba(55, 200, 200, 0.486), rgba(55,200,200,0) 70%),
                    linear-gradient(336deg, rgba(0, 0, 255, 0.466), rgba(0,0,255,0) 65%);
        cursor: pointer;
        transition: 0.3s;
    }
    .cardListPokemon:hover{
        background: linear-gradient(237deg, rgba(0, 255, 64, 0.7), rgba(255,0,0,0) 35%),
                    linear-gradient(127deg, rgba(55,200,200,.8), rgba(55,200,200,0) 50%),
                    linear-gradient(336deg, rgba(0,0,255,.9), rgba(0,0,255,0) 55%);
        
    }
    .cardListPokemon img:hover{
        padding: .1rem;
    }

</style>
