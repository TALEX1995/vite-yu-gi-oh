<script>
import { store } from '../data/store.js';
import PokemonCard from './PokemonCard.vue';
import FilterSelect from './FilterSelect.vue';
import TextFilter from './TextFilter.vue';
import axios from 'axios';


export default {
    data() {
        return {
            store,
        }
    },

    methods: {
        typeFilterPokemon(tipo) {
            axios.get(`https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?eq[type1]=${tipo}`).then(res => {
                store.isLoading = true;
                store.pokemons = res.data.docs;
            }).catch(err => {
                console.log(err.message)
            }).then(() => {
                store.isLoading = false
            })
        },

        resetPokemonFilter() {
            axios.get('https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons').then(res => {
                store.isLoading = true;
                store.pokemons = res.data.docs;
            }).catch(err => {
                console.log(err.message)
            }).then(() => {
                store.isLoading = false
            })
        },

        nameFilterPokemon(name) {
            axios.get(`https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?q[name]=${name}`).then(res => {
                store.isLoading = true;
                store.pokemons = res.data.docs;
            }).catch(err => {
                console.log(err.message)
            }).then(() => {
                store.isLoading = false
            })
        }
    },

    components: { PokemonCard, FilterSelect, TextFilter }
}
</script>

<template>
    <!-- Filter based on pokemon type -->
    <h3 class="m-3">Sceglio il tipo di pokemon:</h3>
    <div class="d-flex m-3">
        <FilterSelect :filtered-array="store.pokemonType" @value="typeFilterPokemon" />
        <button class="btn btn-primary ms-3" @click="resetPokemonFilter">Annulla Filtro</button>
    </div>

    <!-- Filter based on pokemon name -->
    <div class="d-flex m-3">
        <TextFilter placeholder="Inserisci il nome del Pokemon" @form-submit="nameFilterPokemon" />
        <button class="btn btn-primary ms-3" @click="resetPokemonFilter">Resetta</button>
    </div>

    <!-- Loader -->
    <div v-if="store.isLoading" class="fs-1">LOADING ...</div>

    <!-- Pokemon Card -->
    <div v-else class="row row-cols-2">
        <div v-for="{ imageUrl, name, type1, type2, color, generation, hp, atk, def } in store.pokemons" class="col d-flex">
            <PokemonCard :pokemonImg="imageUrl" :name="name" :type1="type1" :type2="type2" :color="color"
                :generation="generation" :hp="hp" :atk="atk" :def="def" />
        </div>
    </div>
</template>


