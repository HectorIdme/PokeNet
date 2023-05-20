<script>
import CardPokemon from './CardPokemon.vue';

export default{
    name: 'PokemonList',
    components: {
        CardPokemon
    },
    inject: ['allPokemons'],
}

</script>

<template>
    <div class="card-list-pokemon container">
        <div v-for="pokemon in allPokemons" :key="pokemon.id">
            <CardPokemon :pokemon="pokemon" />
        </div>
    </div>
</template>