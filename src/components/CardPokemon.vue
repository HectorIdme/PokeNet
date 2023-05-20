<script>
import { RouterLink } from 'vue-router'

export default{
    name: 'CardPokemon',
    props: {
        pokemon: Object
    }
}

</script>

<template>
    <div class="card shadow">
        <RouterLink :to="`/pokemon/${pokemon.id}`" className='card-pokemon'>
            <div class="card-img">
                <img :src="pokemon.sprites.other.dream_world.front_default" :alt="`Pokemon ${pokemon.name}`">
            </div>
            
            <div class="card-info">
                <span class="pokemon-id">N° {{pokemon.id}}</span>
                <h3>{{ pokemon.name }}</h3>
                <div class="card-types">
                    <div v-for="item in pokemon.types" :key="item.slot">
                        <span :class="item.type.name">
                            {{ item.type.name }}
                        </span>
                    </div>
                </div>
            </div>
        </RouterLink>
    </div>

</template>

<style scoped>
.card {
 border-radius: 10px;
 background: white;
 transition: border-radius 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.shadow {
 box-shadow: inset 0 -3em 3em rgba(0,0,0,0.1),
             0 0  0 2px rgb(190, 190, 190),
             0.3em 0.3em 1em rgba(0,0,0,0.3);
}
</style>