<template>
    <v-container>
        <v-layout row wrap align-center justify-center>
            <v-btn
                color="success"
                v-if="this.paginaActual > 1"
                @click="$emit('previousPage')"
            >Previous</v-btn>
            <v-btn
                v-if="this.paginaActual !== this.paginas"
                color="success"
                @click="$emit('nextPage')"
            >Next</v-btn>
        </v-layout>
    </v-container>
</template>

<script>
import axios from "axios";
export default {
    props: {
        paginaActual: Number,
        total: Number,
        limit: Number
    },
    computed: {
        paginas() {
            return Math.ceil(this.total / this.limit);
        }
    }
    // mounted(){
    //     this.paginas = Math.ceil(this.total / this.limit);
    // }
};
</script>
