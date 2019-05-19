<template>
    <v-container>
        <v-layout text-xs-center row wrap>
            <v-flex xs12>
                <v-img
                    :src="require('../assets/pokemon-logo.png')"
                    class="my-3"
                    contain
                    height="200"
                ></v-img>
            </v-flex>
        </v-layout>
        <v-layout row wrap>
            <Pokemon v-for="(pokemon, index) in pokemonList" :key="index" :pokemon="pokemon"/>
        </v-layout>
        <Pagination :paginaActual="paginaActual" :total="total" :limit="limit" @nextPage="nextPage()" @previousPage="previousPage()" />
    </v-container>
</template>

<script>
import axios from "axios";

//Components
import Pokemon from "./Pokemon";
import Pagination from "./Pagination";

export default {
    components: {
        Pokemon,
        Pagination
    },

    mounted() {
        this.findPokemon();
        this.nextPage();
        this.previousPage();
    },
    methods: {
        async findPokemon() {
            const pokeList = await axios.get(this.baseURL);
            this.total = pokeList.data.count;
            this.pokemonList = pokeList.data.results;
        },
        nextPage() {
            this.offset += this.limit;
            this.paginaActual++                   
        },
        previousPage() {
            this.offset -= this.limit;
            this.paginaActual--;                        
        }
    },
 
    data() {
        return {
            pokemonList: [],
            offset: 0,
            limit: 20,
            total: 0,
            paginaActual: 1,            
            baseURL: `https://pokeapi.co/api/v2/pokemon/?offset=${this.offset}?limit=${this.limit}`
        };
    },
};
</script>

<style>
</style>
