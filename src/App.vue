<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './data/store.js';
export default {
    components: { AppHeader, AppMain },


    created() {
        axios.get('https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons').then(res => {
            store.isLoading = true;
            store.pokemons = res.data.docs;
        }).catch(err => {
            console.log(err.message)
        }).then(() => {
            store.isLoading = false
        })
    }
}
</script>

<template>
    <div class="container">
        <AppHeader />
        <AppMain />
    </div>
</template>

<style></style>