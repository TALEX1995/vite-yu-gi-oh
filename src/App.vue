<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './data/store.js';
const apiPokemonEndpoint = 'https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons';
export default {
    components: { AppHeader, AppMain },


    created() {
        axios.get(apiPokemonEndpoint).then(res => {
            store.isLoading = true;
            store.pokemons = res.data.docs;
        }).catch(err => {
            console.log(err.message)
        }).then(() => {
            store.isLoading = false
        });

        axios.get(`${apiPokemonEndpoint}/types1`).then(res => {
            store.pokemonType = res.data
        }).catch(err => {
            console.log(err.message)
        })
    },


}
</script>

<template>
    <div class="container">
        <AppHeader />
        <AppMain />
    </div>
</template>

<style></style>