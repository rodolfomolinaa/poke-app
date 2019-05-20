<template>
    <v-flex xs4 md3 lg2 class="pa-3">
        <div v-if="!info">
            <v-card class="pokemon">
                <v-responsive class="pt-4">
                    <v-img aspect-ratio="2.75" src height="200px">
                        <v-progress-circular :size="70" :width="7" indeterminate color="primary"></v-progress-circular>
                    </v-img>
                </v-responsive>
                <v-card-title primary-title>
                    <div>
                        <h1 class="headline mb-0">{{pokemon.name}}</h1>
                    </div>
                </v-card-title>
            </v-card>
        </div>
        <div v-else>
            <v-card>
                <v-img :src="info.sprites.front_default"></v-img>
                <v-card-title primary-title>
                    <div class="pokemon-data">
                        <h1 class="mb-0">{{info.name}}</h1>
                        <!-- <ul clas>
                            <li v-for="(pokeType, index) in info.types" :key="index" >
                                {{pokeType.type.name}}
                            </li>
                        </ul> -->
                    </div>
                </v-card-title>
            </v-card>
        </div>
    </v-flex>
</template>

<script>
import axios from "axios";
export default {
    props: ["pokemon"],
    data() {
        return {
            info: null
        };
    },
    async created() {
        const { data } = await axios.get(this.pokemon.url);
        this.info = data;
    }
};
</script>

<style lang="stylus" scoped>
.v-progress-circular {
    margin: 3rem;
}

.v-card {
    border-radius 20px;
    background-color white
    box-sizing border-box
    text-align center
}

.v-card:hover {
    background-color #FFE9E1
}

ul.pokemon-type {
    list-style-type square
}


.pokemon-data {
    font-size 10px
    word-wrap break-word
    text-transform capitalize
    position sticky
    width 100%
}

</style>
