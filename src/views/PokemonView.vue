<script>
import Loader from '../components/Loader.vue';

export default{
    name: 'PokemonView',
    components:{
        Loader
    },
    data(){
        return {
            pokemon: {},
            loading: true
        }
    },
    beforeMount(){

        const getPokemonByID = async(id) => {
            const baseURL = 'https://pokeapi.co/api/v2/'
            const res = await fetch(`${baseURL}pokemon/${id}`); 
            const data = await res.json();
            return data;
        }

        const fetchPokemon = async(id) => {
            const data = await getPokemonByID(id);
            console.log("data: ",data);
            this.pokemon = data;
            this.loading = false;  
        }
        
        fetchPokemon(this.$route.params.id);
    }
}

</script>

<template>

    <main class='container main-pokemon'>
        <div v-if="loading">
            <Loader />
        </div>
        <div v-else>
            <div class='header-main-pokemon'>
                <span class='number-pokemon'>#{{pokemon.id}}</span>
                <div class='container-img-pokemon'>
                    <img :src="pokemon.sprites.other.dream_world.front_default" :alt="`Pokemon ${pokemon?.name}`" />
                </div>

                <div class='container-info-pokemon'>
                    <h1>{{pokemon.name}}</h1>
                    <div class='card-types info-pokemon-type'>
                        <div v-for="item in pokemon.types" :key="item.slot">
                            <span :class="item.type.name">
                                {{ item.type.name }}
                            </span>
                        </div>
                    </div>
                    <div class='info-pokemon'>
                        <div class='group-info'>
                            <p>Altura</p>
                            <span>{{pokemon.height}}</span>
                        </div>
                        <div class='group-info'>
                            <p>Peso</p>
                            <span>{{pokemon.weight}}KG</span>
                        </div>
                    </div>
                </div>
            </div>

            <div class='container-stats'>
                <h1>Estadísticas</h1>
                <div class='stats'>
                    <div class='stat-group'>
                        <span>Hp</span>
                        <div class='progress-bar'></div>
                        <span class='counter-stat'>
                            {{pokemon.stats[0].base_stat}}
                        </span>
                    </div>
                    <div class='stat-group'>
                        <span>Attack</span>
                        <div class='progress-bar'></div>
                        <span class='counter-stat'>
                            {{pokemon.stats[1].base_stat}}
                        </span>
                    </div>
                    <div class='stat-group'>
                        <span>Defense</span>
                        <div class='progress-bar'></div>
                        <span class='counter-stat'>
                            {{pokemon.stats[2].base_stat}}
                        </span>
                    </div>
                    <div class='stat-group'>
                        <span>Special Attack</span>
                        <div class='progress-bar'></div>
                        <span class='counter-stat'>
                            {{pokemon.stats[3].base_stat}}
                        </span>
                    </div>
                    <div class='stat-group'>
                        <span>Special Defense</span>
                        <div class='progress-bar'></div>
                        <span class='counter-stat'>
                            {{pokemon.stats[4].base_stat}}
                        </span>
                    </div>
                    <div class='stat-group'> 
                        <span>Speed</span>
                        <div class='progress-bar'></div>
                        <span class='counter-stat'>
                            {{pokemon.stats[5].base_stat}}
                        </span>
                    </div>
                </div>
            </div>
        </div>

		</main>

</template>